<!-- C -->
# 自己修復的なインフラ

- CIでのインフラ更新
- Railsのデプロイ

IAMユーザよりIAMロールの方が良い

- IAMユーザのキーを最小限に保つ
- アカウント切り替えが便利

## 実現したいもの

1. PRにdry-runの結果
2. マージ後にCircleCIを動かす
  - Codecommit
  - Codebuild terraform/apply
3. 良さそうならprodへ反映

- Runnning terraform in automation
  - workspace?

