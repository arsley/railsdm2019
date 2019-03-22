<!-- A -->
# Red-Black Tree for Ruby

- wovn.io

インメモリ800万個の中から最小値を見つける
- 頻繁に削除/追加が行われる
- redisなし
- Rubyのみ

SortedSet
- 通常の実装ではHash
- あれば `gem rbtree` を使う
- Array#sort!を都度行なっていたらしい
- 最悪計算量はO(n^2)

Rbtree gem?
- Red-Black Treeの実装を提供するC extension gem

赤黒木
- 2分木
- 各ノードは赤か黒の色を持つ
- 根は黒
- ...
- 更新がないようなもの(辞書)であればAVLの方が適している

* RBTreeで優先度付きキューが簡単に使える
* 同じく転置インデックス検索
  * Hashはkeyが辞書順になっていないので `lower_bound` などでの検索が強い

Red-Black Treeは実装が難しい
- Left-lening Red-Black Tree
- 赤黒木を2-3-4木で表現する過程で必要となる制約を加えた
- これによりチェックするべき制約が減って実装が簡素になった

Left-leaning Red-Black TreeはRed-Black Treeより遅かった
