# mojxmltools

登記所備付地図XMLデータ(moj-xml)から、各種要素を抽出してタブ区切りファイルとして出力するツールです。

現時点では自家用レベルなので、使い勝手は悪いです。
パラメタ等今後整備していきます。　
フォルダ内のファイルをまるごと処理する動作となります。


## mojxml2csv
csvじゃなくてtsvなので名前変えようと思ってたのですが、tsvって（私の周りでは普通に使う言葉だけど）分からない人が多いという調査結果もあるので（私調べ）、名称はcsvのままにしておきます。 Character Separated Values。

### 使用法
パラメタ処理は雑なので、最後のスラッシュの要否等は何回か動かしながら把握してください（ぺこり）。今後変わります。

```
usage: mojxml2csv.py [-h] [-i <INPUT_FOLDER>] [-o <OUTPUT_FOLDER>] [-r <RELEASE_VERSION_NAME>] [--profile]

mojxml2csv: Extracting from mojxml files to tab-separated files

optional arguments:
  -h, --help            show this help message and exit
  -i <INPUT_FOLDER>
  -o <OUTPUT_FOLDER>
  -r <RELEASE_VERSION_NAME>
                        Release version. It is used for column value and filename. ex)202404
  --profile             Execute with cProfile.
```

例）python3 mojxml_extract_pointinfo.py -i data202404 -r 202404 -o outtmp --profile


### 実行時間とサイズの例
実行時間はかなりかかります。
都道府県単位で処理する場合は、小さい都道府県で40分程度、大きいと2～3時間かかります。
lxmlモジュールをインストール済みの場合、そちらを使用して多少高速に動作します（pipでインストール可能です）。

- 出力ファイルサイズ例
    - 千葉県の例

```
-rwxrwxrwx 1 sakaik docker  3061946874 Apr 25 16:48 12_202404_11points_data.tsv*
-rwxrwxrwx 1 sakaik docker  9089287910 Apr 25 16:48 12_202404_12curves_data.tsv*
-rwxrwxrwx 1 sakaik docker  4317191734 Apr 25 16:48 12_202404_13surface_data.tsv*
-rwxrwxrwx 1 sakaik docker  4920832173 Apr 25 16:48 12_202404_22line_info.tsv*
-rwxrwxrwx 1 sakaik docker   829058324 Apr 25 16:48 12_202404_23fude_info.tsv*
-rwxrwxrwx 1 sakaik docker    41731175 Apr 25 16:48 12_202404_31zukaku_info.tsv*
-rwxrwxrwx 1 sakaik docker    32488298 Apr 25 16:48 12_202404_32zukaku_ref.tsv*
```

