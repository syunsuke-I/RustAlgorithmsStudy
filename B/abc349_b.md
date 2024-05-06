
# 解いた問題
https://atcoder.jp/contests/abc349/tasks/abc349_b

# 提出コード

```rust
use proconio::input;
use std::collections::HashMap;

fn main() {
    input! {
        s: String,
    }

    let mut freq = HashMap::new();

    // 各文字の出現回数をカウント
    for ch in s.chars() {
        *freq.entry(ch).or_insert(0) += 1;
    }

    let mut count_freq = HashMap::new();

    // 出現回数ごとの文字種類数をカウント
    for &count in freq.values() {
        *count_freq.entry(count).or_insert(0) += 1;
    }

    // 各出現回数が0または2種類の文字であるかをチェック
    let is_good_string = count_freq.values().all(|&x| x == 0 || x == 2);

    // 結果出力
    println!("{}", if is_good_string { "Yes" } else { "No" });
}

```

# ポイント
* or_insert でデフォルト値が設定できる
