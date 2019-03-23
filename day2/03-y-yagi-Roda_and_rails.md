<!-- B -->
# Roda and Rails

## About Roda

- Routing Tree Web Framework Toolkit
  - MVCにおけるVCの部分だけ
- Sinatraの仲間
  - 階層構造のルーティングができる
- はやい

- Author: Jeremy Evans
  - Sequel
  - Erubi
  - RubyKaigi2019に来るらしい

- bench-micro
- Web Framework Benchmarkers
  - TechEmpower社が提供しているベンチマーカー
  - Ruby以外のも色々ある
  - TechEmpower

- 提供している機能が違いので単純に比較するべきではない

- Roda is a la carte
- Rodaのcoreは最小限の機能しかない
- pluginとして提供している

### But

- あくまでのRodaはルーティングライブラリ
  - rakeタスクなどを自分で作らないといけない
  - Rails + Rodaができないか?

## Rails router

- journey?(parser)
- 複雑なアプリを作成するためには必要な処理だった(Rails Routers)

- 昨今ではAPIエンドポイントとして、GraphQLではPOST一つのみ

## Roda on Rails

- Rackベース
- mountメソッドを使えばRailsのroutingで使える

### 性能検証

- wg/wrk
  - digitaloceanの記事を参照?
- 1.2倍くらい速くなる

### Router

- ActionDispatch::Router::Routeset は差し替え可能
- #endpoint
  - 変えたけどあまり変わらなかった

### Rack Middleware (API-only)

---
- UserがいじっていいものをPublicAPIというらしい
---

- Railsは基本全部入り
- いらないやつもある
  - Sendfileとかも消せる
  - `config.middleware.delete Rack::Sendfile`
- config.ru でRodaに変えればそりゃ速くなる
  - けどRailsでもともと書いてたら書き直しのコストがかかる

### Railsroad-switch

- 指定したリクエストのみrodaで、それ以外はRailsへということができた

## まとめ

- omakase is benri
  - rails newがよしなにしてくれる
- omakaseが自分たちのアプリケーションの機能が完全に一致するとは限らない
- アプリケーションに合わせて、適切なメニューが選べたらいいのではないか
