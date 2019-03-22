<!-- C -->
# サーバーサイドエンジニアも知っておくべきフロントエンドの今

フロントエンドのエコシステム
注目の話題

現在のエコシステム
- TypeScriptが基本
  - できない場合は大抵Vueのせい
  - TS最強らしい(という結論が出た)
- 一般的にはES5
  - IE11を非対応の決断

DOM管理(宣言的View)
- React, Vue, Angular, Elm

「ある場外に対してあるべきDOMを定義する」→を宣言的

lit-html
- googleのpolymerチームが作っているライブラリ
- 仮想DOM

Editor
- VSCode
  - vscode + TS + ESLint + Prettie

Linter
- ESLint
- TSLint(近々、deprecatedになる)

Formatter
- Prettir
- prettir-rubyが開発されているらしい

module bundler
- webpack(webサービス開発)
- rollup(ライブラリ開発)
- pika(rollupのラップ)

test
- Jest
- Jest + Puppeteer(E2E)
  - PuppeteerはChromeをNodeから操作できる
  - celeniumばなれ
  - nightwatch, cylium?

非同期処理
- axios
  - GET以外を使うなら
  - ajaxは今から導入しない

Web components
- polyfillを入れれば使える技術にはなっている
- polyfillの出来が悪い?

仮想DOMは死ぬか?
- 現状はそんなことはない
- ただしWebComponentsで書ければその方がいい(他フレームワークでも使える)

## 注目

- CDM workder
- micro frontends
- PWA
- レンダリング最適化
- web payments/ web authentication

CDN workerは正式名称が(多分)ない

CDN worker
- CDNへのリクエストにフックして走る何か
- AWS Lambda@Edge + CloudFront
- Cloudflare

CDN Workerの熱いところ
- BFFをエッジにおける?

BFF(Backend For Frontend)
- フロントエンドとバックエンドの仲介役
- 立てるならNodeだと嬉しい(Server Side Rendering)
役割の例
- 認証
- API Aggregation
- Server Side Rendering
- Cache

SPAを用いた環境でやりたかったこと・課題
1. FMP/SEOを最適化したい
2. レンダリング済みHTMLをクライアントに投げたい
3. つまりSSRしたい
課題
- SSRにはJS実行環境が必要

1. RTTを高速化したい
2. 通信距離を最短にしたい
3. エッジロケーションで通信を完結したい
課題
- 動的サイトでオリジンサーバでHTMLを作る

CDN Workerなら解決できる?
- エッジロケーションでレンダリング・レスポンスを返せる
- リージョンに特に関係なく速度が出せる
- オリジンサーバへの負荷を最小限にできる

おすすめ?
- Cloudflare Workers

まとめ

エコシステムは成熟している
- 開発体験は向上している
- ライブラリの乱立も落ち着いた
UXに直結する話題が多い
- サーバサイドエンジニアも理解し実践すべき
フロントエンドをフロントエンド技術で管理していないとできない最適化がある
- 最適な設計を考えるならフロントの知識も必要

---

TSの理解
状態管理(MVC1がfluxの原型?)
宣言的View
GoogleDevelopersChannel
GoogleIO
ChromeDevSummit

webpackerを使うことでwebpackを理解できない

Elmは「Haskellキますか」というのと同じ話
