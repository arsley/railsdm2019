<!-- A -->
# DevOps, Immutable Infrastructure, microservices そして Chaos Engineering

DevOpsが言及されてから10年
個別の要素技術はあっても、全体をまとめた話はなかなかない
ActiveRecordはパターン名

Immutable Infrastructure(2013)
- インフラをimmutableにしようね
chad fowler
今ではchefに書いたりする←これをよく忘れる
なので「不変にしよう」という話
Blue-Greenとか使えればいいよね

Blue-Green (2010 martin fowler)
- サーバの不変性ではなく、デプロイの高速化などが主題

microservices(martin fowler)
- 実は組織パターンの話
  - 「1つの小さいチームでやること」
- conwayの法則
- 1つのでかいチームでやっていても意味がない
  - システムを分けているだけで、"マイクロサービス"ではない

急速に流行りすぎた
- microservices prerequisites(martin fowler)
  - rapid provisioning
  - basic monitoring
  - rapid application deployment
  - これら三つができないならmicroserviceを始めるべきではない
- 上記のことはモノリスでも必要なので、整えるべき

the recipe for the world's largest rails monolith
- 20000+ spec
- 1700+ model
- rrrspec
- mamiya

microserviceへ... Docker
- applicationもimmutableを意識することを強制するもの
  - ファイルをサーバにアップロードさせない
    - いつ落ちるのかわからない
  - キャッシュとか学習結果とかもサーバに置かない
    - 同上

container orchestration
- k8s, ecs
- アプリケーションの実行を抽象化(docker run)
  - アプリケーションごとのサーバを構成する必要がなくなり、コンテナの実行環境のみ用意すれば良い
- オーケストレーションは「人の手で扱いきれなくなったら」手を出すべき

microservice + containerでポータビリティが向上した
- 個々のサービスは簡潔になったが、全体は複雑なまま
- ここまでくると、container間の連携が課題になる

servicemesh
- data-planeとしてEnvoy proxyを使う
- サービス間通信をEnvoyProxyを利用することで、この設定ファイルを見れば全てわかる
  - 今まではアプリケーションコードの中にしかなかった

pactを利用してサービス間通信のミスをテストしようと思った(がやめた)

Chaos Engineering
- 分散システムにおいてシステムが不安定な状態に耐えることのできる環境を構築するための検証の規律
- *サーバを落とすことではない*

steady stateを決める
- サービスの定常状態を計測できるようにする

Netflix
- 毎秒どのくらいのユーザーが動画見始めたか
- 毎秒どのくらいのユーザーがサインアップしたか
Cookpad
- レシピ閲覧数と検索数の比

fault injection testing?
- サービス間通信
- 過剰にテストを書くのではない。影響範囲を把握し最小限にする
- マイクロサービスを採用するチームはサービスがUXにどう影響するか常に検討する
