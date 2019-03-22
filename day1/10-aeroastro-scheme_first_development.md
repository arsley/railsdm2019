<!-- B -->
# Rails meets Protocol Buffers - For Schema First Development

ゲーム開発でRailsを選んだ理由
- ランタイムにおいて許容可能なオーバーヘッドを加味すれば開発に最適
- DeNAにはRubyのAseetがあった
- Railsは遅いが、許容可能

理想的なスキーマファースト開発とは

Traditional Bad Development
- ドキュメントの問題
  - これで何かを伝えようとするのにコストがかかる
- スケジュール
  - バックエンド→フロントエンドは遅くなりがち
- コミュニケーションの取り方
  - バックエンドとフロントエンドを切り分けたことによる

スキームファースト開発
APIでいえば
- バックエンド・フロントエンドチームによらない設計書の共有?

理想的なスキーマ開発とは
- スキーマを作り、設計に対して合意を取る
- 自動でコード・ドキュメント・モックAPIができてほしい
- ここから開発を始める
- 何か変更点があればスキーマ制作へたちかわる

protocol buffer
- by Google

in-house scheme
- SDKを作るもの
  - I/F (Interface) 部分のやりとりについて自動生成する

システム概要
- Bodyスキーマをprotocol bufferで

スキーマ開発の最終目標は「プロダクトの完成」であって「完璧なスキーマの作成」ではない
「不完全なスキーマ」から始める
- クオリティを上げる
  - 初期プロトタイプの生成
- コストを下げる
- 提供を早く

Protocol Buffer as Scheme
- 簡素な記法

Protocol Buffer as Serialization
- メモリのFootprintが小さい
- バイナリやデータに対して自然に扱える
- 簡単にリファクタリングできる
- Serializetion/Deserializationしやすい

RailsにProtocolBufferを組み込む

Request
1. MIME Typeに追加する
2. 他のparserを全て外す
3. `before_action` にて適切なparseを行う
4. JSONとしてrenderする

Response
1. ()
2. `respond_to` を用いる
3. JSONをrender

Controller
1. paramsをhashとして読む
2. ()
3. fields?

掲げたものは「理想的な」開発であって、課題はある
- もっとスケーラブルなアーキテクチャであってほしい
- 各社員がそれぞれの得意分野に専念できるように
- ...

---

難しいというか早いというか
