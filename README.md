# sumikko-brain
すみっコぐらしのキャラクターをモチーフにRustで実装した派生BF言語です。

元のBF言語とは違う仕様でだったり、追加でオリジナルのコマンドが増えていたりします。

## Requirement

- Cargo 1.52

## How to Build & Execute

- ビルド方法

```
$ cargo build
```

- sumikko-brainの実行方法

```
cargo run <smbrファイルのパス>
```

## Usage

SMBR(summiko-brainを略してそう呼んでいます...)を記述したファイルを引数に渡すことで実行できます。

- hello_world.smbrの中身

```
ぺんぎん? ぺんぎん? ぺんぎん? ぺんぎん? ぺんぎん? 
    ぺんぎん? ぺんぎん? ぺんぎん? ぺんぎん?

えびふらいのしっぽ
    しろくま
        ぺんぎん? ぺんぎん? ぺんぎん? ぺんぎん? ぺんぎん? 
            ぺんぎん? ぺんぎん? ぺんぎん?
    しろくま
        ぺんぎん? ぺんぎん? ぺんぎん? ぺんぎん? ぺんぎん? 
            ぺんぎん? ぺんぎん? ぺんぎん? ぺんぎん? ぺんぎん? 
            ぺんぎん?
    しろくま
        ぺんぎん? ぺんぎん? ぺんぎん?
    しろくま
        ぺんぎん?
    とんかつ とんかつ とんかつ とんかつ
        とかげ
あじふらいのしっぽ

しろくま ねこ // H
しろくま ぺんぎん? ぺんぎん? ねこ // e
ぺんぎん? ぺんぎん? ぺんぎん? ぺんぎん? ぺんぎん?
    ぺんぎん? ぺんぎん? ねこ // l
ねこ // l
ぺんぎん? ぺんぎん? ぺんぎん? ねこ // o
しろくま ぺんぎん? ぺんぎん? ぺんぎん? ぺんぎん? 
    ぺんぎん? ねこ // (space)
とんかつ とんかつ 
    ぺんぎん? ぺんぎん? ぺんぎん? ぺんぎん? ぺんぎん? 
    ぺんぎん? ぺんぎん? ぺんぎん? ぺんぎん? ぺんぎん? 
    ぺんぎん? ぺんぎん? ぺんぎん? ぺんぎん? ぺんぎん? 
    ねこ // W
しろくま ねこ // o
ぺんぎん? ぺんぎん? ぺんぎん? ねこ // r
とかげ とかげ とかげ とかげ とかげ 
    とかげ ねこ // l
とかげ とかげ とかげ とかげ とかげ 
    とかげ とかげ とかげ ねこ // d
しろくま ぺんぎん? ねこ // !
しろくま ぺんぎん? ねこ // ¥n
```

- smbrをコンパイルして、"Hello World!"する

```
$ ./target/debug/sumikko-brain ./sample/hello_world.smbr
Hello World!!
```

## SMBR Command List

- しろくま <br>
　右の方に移動するよ!! <br>
　(ポインタをインクリメントする)

- とんかつ <br>
　左の方に移動するよ!! <br>
　(ポインタをデクリメントする)

- ぺんぎん? <br>
　すみっコを一匹追加するよ!! <br>
　(ポインタが指す値をインクリメントする)

- とかげ <br>
　すみっコを一匹減らすよ!! <br>
　(ポインタが指す値をデクリメントする)

- ねこ <br>
　すみっコの数を文字で表示するよ!! <br>
　(ポインタが指す値をchar型で出力する)

- ざっそう <br>
　すみっコの数を数字で表示するよ!! <br>
　(ポインタが指す値をu8型で出力する)

- たぴおか <br>
　すみっコの気持ちを読み取るよ!! <br>
　(入力から1byte読み込んで、ポインタが指す値に代入する)

- えびふらいのしっぽ <br>
　すみっコ達との思い出を作るよ!! <br>
　(ポインタが指す値が0なら、対応する"あじふらいのしっぽ"の直後にジャンプする)

- あじふらいのしっぽ <br>
　すみっコ達との思い出に浸るよ!! <br>
　(ポインタが指す値が0でないなら、対応する"えびふらいのしっぽ"の直後にジャンプする)

- ふろしき <br>
　ランダムにすみっコを呼んでくるよ!! <br>
　(0〜255の乱数を発生させ、ポインタが指す値に代入する)