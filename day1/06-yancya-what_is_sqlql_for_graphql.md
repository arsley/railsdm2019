<!-- B -->
# SQLQL は GraphQL にとって、何なのか

SQLQLの基礎・考え方
- 特定のURLに対してSQLを送ることでクエリを実行するもの

気をつけたいこと
サーバ側のRDBMSの処理系は使いたい
- postgresql
でもSQLQLで送られてきたものをむやみに実行したくない

sqlql/sqlql-sampleなるアプリがある
- 鍵付きユーザー・鍵付き投稿という概念がある

CTE(Common Table Expressions)
- インラインのView
- サブクエリに名前をつけて、クエリ中でなんども使える
- 既存のデフォルトスキーマ(public)のテーブルを上書きすることができる
- シャドウイング↓

```
WITH users AS (
  SELECT id, name FROM users WHERE id = ? OR privacy = false
)
SELECT * FROM users
```

- CTEによりあらかじめ射影できる

問題点
- Mutation(DELETE UPDATEなど)が邪魔
- スキーマ修飾・システムカタログテーブルなどへのアクセス制限
- 無限ループ
  - チューリング完全の言語(SQL)

複数DB
- Rails6.0からreplica属性のサブコネクションの設定が簡単に設定できるようになった
- ただ、 `WITH` を弾いてしまう
- モンキーパッチしたけどやっぱり危ない(WITHの中でUPDATEはできる)
- DBユーザーを作る
  - config/database.ymlに設定を加える

テーブルホワイトリスト
- gem pg_query

無限ループ対策
- timeoutをつける

SQLQLの核?
- インピーダンスミスマッチ
- Object → Relation

インピーダンスミスマッチ
- SQL
- 表とオブジェクトで対応するのなんかおかしくない?ということ

Relation to Object
- JSON_AGGという関数がPGにあるらしい
  - SQLだけでJSONレスポンスを作れる

<!-- 力尽きた -->
