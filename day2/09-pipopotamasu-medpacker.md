<!-- C -->
# Railsフロントエンドボイラープレート「medpacker」の紹介

## medpacker?

- medpeer-inc/medpacker
- RoRのFrontend boilerplate

- pure webpack
  - no asset pipeline
- preinstalled libraries
 - unify libraries
- easy and fast install

## why developed?

1. webpacker, assetpipeline辛い
2. ライブラリ統一したい
3. 早く開発したい

### assetpipeline cons

- モダンなフロント環境への更新がきつい
  - npmとか使いたい
  - 事前ビルドとか入ると大変
- sprockets遅い
- rails-way frontend
  - gemが関わる
  - フロントもバックもごちゃごちゃ

### webpacker cons

- 抽象的なconfig
  - ymlであること
  - 複雑な処理をさせたいと面倒
- 初期コンフィグが貧弱?

### ライブラリの統一?

- フロントの人は外注であることが多い
  - でももらったコードはReactだった...(Vueがよかった)

- 「これを使ってね」ということが言える

### サービスを早く上げたい

- 会社の戦略上、新しいプロダクトをたくさん作られる
- `rails new` するたび0から作るの大変
  - だからこそboilerplateを用意しておきたい

## medpacker

- Rails Application Template

### Read assets

- `javascript_bundle_tag`
  - `javascript_include_tag` 使ってる?
- `stylesheet_bundle_tag`

## E2E test

- specに `js: true` が必要

---

質問: `javascript_bundle_tag` にて `javascript_include_tag` を使っているということはsprockets依存を完全になくしたわけではないということですか？
「sprocketsが遅い」ということだったので少し違和感を覚えて... 

回答: sprocketsとは関係ない。ということでヘルパーとして使っている
