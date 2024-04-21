
# 解いた問題

https://atcoder.jp/contests/abc348/tasks/abc348_b

# 所管

* powfで平方根できる
* `Vec::new()` 可変長の変数を定義できる
* ベクタは分割代入できる

# 提出したコード

```rust
use proconio::input;

fn main() {
    input! {
        n: usize, 
    }

    let mut pairs = Vec::new();

    for _ in 0..n {
        input! {
            x: i32,
            y: i32,
        }
        pairs.push((x as f64, y as f64));
    }

    for i in 0..n {
        let mut max_value: f64 = 0.0;
        let mut max_point = 0; 
        let (x1, y1) = pairs[i];
        
        for j in 0..n {
            if i != j {
                let (x2, y2) = pairs[j];
                let root = ((x1 - x2).powf(2.0) + (y1 - y2).powf(2.0)).sqrt();
                if root > max_value {
                    max_value = root;
                    max_point = j + 1; 
                }
            }
        }
        println!("{}", max_point);
    }
}

```
