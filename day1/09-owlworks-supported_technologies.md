<!-- B -->
# AskDoctorsの13年目を支える技術

AskDoctors
- 24h365毎日いつでも医者に体調について相談できたりする
- 2005からある

.present?(2005年)
- iPhone, Chrome, jQuery => false

JavaのGeneratorというFramework

Butgtracker
- Jira

JSFramework
- Vue.js

なんだかんだでデータなどは共有したい
- WEBAPI + CoreAPI

PCとSmartPhone(SP)の見た目を統合しよう
- Rails

開発期間が長いので...
- Batchの内容がわからない
- ドキュメントのありかはどこに?

ガラケー向きのサービスは一旦開発を凍結
そうすると...
- CoreAPIの問題が見えてくる
1. 書けるコード量が少ない
2. APIのトランザクション
3. APIの設計がそもそも難しいよね
  - これらはマイクロサービスアーキテクチャの欠点だよね
  - ただこの時期にはこれを指す言葉がなかったため良い解決策がなかった

人数が少ない中サービスをリプレースしていくと...
- メンテのされないゾンビサービスが残ってしまう
  - バッチが残っているが読めない
- serverのconfigが読めない

Reorganize(再編の時期)
- 法人向けとかでユーザーは増えていた

スケールアップを行う
- 開発環境
  - e2e test
  - migration(flyway)
  - consolidate batch(digdag)
- Application
  - solr => elasticsearch
  - cache strategy
  - DB scaleup
  - Docker(kubernetesにしたいそう)

↑の内容は(普通の人には)わかりにくいため延期されがち
しかし、「エンジニアの時間」が得られるようになる

歴史は教えてくれる
1. (力尽きた)
2. サービスのコンセプトはなんだったか
3. (力尽きた2)
