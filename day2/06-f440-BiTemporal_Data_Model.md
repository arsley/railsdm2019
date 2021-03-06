<!-- B -->
# 操作履歴/時点指定アクセスの実現 - BiTemporal Data Model の実践

## SmartHR

- 人事・労務に関する手続きの自動化を目指すクラウド型ソフトウェア

## 人事DB

- ライフイベントに応じてレコードの内容が変わる
  - 結婚
  - 異動
  - etc.
- 細心の注意を払わないといけない(デリケートな情報なので)

- 変遷するデータの履歴を残したい
- ↑ができるようになると、ある時点での一覧表示などもしたい

## RoR * 履歴

- Railsのデフォルトだと最新更新日だけが残る
  - `t.timestamps`
- 消えた情報は跡形もなくなる

### 論理削除

- `gem paranoia` ?
- `deleted_at` を追加

### バージョニング

- 更新
  1. 現行レコードを論理削除
  2. 新しいデータを挿入?
- 検索
  - `{ deleted_at: nil }`なものから探したりそうじゃなかったり
 
### 履歴テーブル

- 特定のトリガーでコピー

- Pro: アプリケーションを修正しなくとも良い etc.
- Con: 現行データと履歴を混ぜると厳しい

## BiTemporal Data Model

### non-temporal

- 最新情報のスナップショットを表現
  - Default Rails

### uni-temporal

- 有効期間を持たせる

- 「実はこうだった」のような過去の事象に対する変更記録を保存できない
  - 11/1に「10/11-10/15の間はAさんは部長でなく係長だった」という指摘を受けた

### bi-temporal

- システム的な操作履歴としてさらにカラムを追加する

利用するために `ActiveRecord::BiTemporal` を作ったらしい

## 導入した

### 辛いポイントs

- ユニーク制約でおかしい
  - DBレベルで生合成を担保すべき
  - PGなら範囲型がある
- primary key
  - 生の主キーを使っている一部のgemは壊れる
  - monkey path or 諦め
- sort
  - `#first, #last` は暗黙的に `order by #{primary_key}` しているらしい
- 性能

