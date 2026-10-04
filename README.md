# keycloakの検証用コンテナ群

## 運用コマンド

起動

```sh
docker compose up -d
```

アクセス

```sh
http://localhost:8080
```

停止

```sh
docker compose down -v
```

## Tips

### JDBCとは

Java Database Connectivityの略。
KeycloakはJava製なので、PostgreSQLへ接続するときも `JDBC` というJava標準の仕組みを使用する。

### コマンド

keycloak起動コマンド（開発用）は

```sh
start-dev
# /opt/keycloak/bin/kc.sh start-dev
```

keycloak起動コマンド（本番用）は

```sh
start
# /opt/keycloak/bin/kc.sh start
```

### RealmJSONのエクスポート

コンテナに接続

```sh
docker exec -it keycloak-test bash
```

realmを指定してjsonファイルをエクスポート

```sh
REALM=${realm}
/opt/keycloak/bin/kc.sh export --realm $REALM --file /tmp/tmp-realm.json
```

接続を切断

```sh
exit
```

ローカルにコピー

```sh
docker cp keycloak-test:/tmp/tmp-realm.json ./tmp-realm.json
```
