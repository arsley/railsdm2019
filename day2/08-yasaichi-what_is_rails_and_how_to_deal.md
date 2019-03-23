<!-- C -->
# Ruby on Railsの正体と向き合い方

`self.inspect`

## 背景目的

- 今まで「Railsとの向き合い方」で話して来た
- Railsの限界に対してコード・アーキテクチャレベルでどうするか

- Railsはいつ、なぜ限界を迎えるのか
- ↑より既存の対処法を提示する

## Railsの招待

- Basecamp
- 早くてきれい
- 密結合

### Basecamp

- Basecamp社の提供するプロジェクト管理ツール
  - 元々は社内ツールだった
- 技術選定・プログラミング全てやった(DHH)
  - 自分の仕事をよりよく、より早く(Rails)

* 「少人数のスタートアップでのプロダクト開発」

### 早くてキレイ

- DHHはPHP, Javaを書いていた
  - 試しにRubyを使ってハマった
- 「早いけど汚い」「遅いがキレイ」

* PHPと同じくらい早く、Javaのように堅牢でクリーンなものを目指した

- 早くてキレイを実現するためにDHHも何かを妥協しているはず
  - 何かしらの制約を置いている

### 密結合(妥協点)

- 柔軟さ
  - CoC
  - 柔軟そうと引き換えに考える・書く量を減らした
- 疎結合

## 密結合度合いの比較

- RailsとHanamiで比較
  - クリーンアーキテクチャ

### クリーンアーキテクチャ

- 緑から内側を書く
  - Entities
  - Application Business Rules(Interactor)
  - Interface Adapters(Controller, Presenter, Repository)

rails model = hanami interactor
- RailsのModelは特定のユースケースと密結合

- RailsのModelでクリーンアーキテクチャをラップしている

(Application Modelのある風景)

## Railsの招待

- URLで表されるリソースからDB上のテーブルまでが密結合をする構造を作った
- ...

### 「密結合は悪?」

- ...

## Railsの限界

- あるモデルが複数の異なるユースケースでCRUD操作されるようになった時
- Modelに書かれたユースケースと密結合しているため

### 限界の表出

- 特定の条件でvalidationをスキップする
- Controller内にtransactionを書く
  - ModelだけでCRUDが扱えなくなった

## Railsとの向き合い方

- コードレベル
- アーキテクチャレベル

### コードレベル

- ActiveRecordの分割
- ApplicationModelの導入
- Form/Serviceの導入

* Controller or Actionと1:1対応する新しいそうを作るのと変わらない

* ユースケース個数の処理を書く層を作り切り分ける

### アーキテクチャ

- アプリケーションが対象とするドメインを小さくする
- 複数のサブシステムへ分ける

### 現状

- 独立性の高いものはサブシステムとして作る
  - アプリケーションが対象とするドメインが小さくなるとRailsを選ぶか?
- SoEとSoRへ
  - 「本体」を組織構造と一致するようにサブシステムに分割
  - Front,Backも密結合してる
  - 次はRailsAPI + BFFで分ける

## まとめ

- DHHが解決したかったこと
  - 少人数の速さ
- Railsのアプローチ
  - URLから一本道で使えるようにした

---

書き逃したくさんある
