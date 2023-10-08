# data

OpenVCalの定義レポジトリへようこそ！

このレポジトリは**アルファ**版です。実証実験には適していますが、本番環境で使うには向いていません。

## スキーマ
明記されていない限り、すべての値は`null`であることはない。また、省略することもない。

* `$schema`: JSON schemaへのURLを格納する予定
* `metadata`: メタデータ
* `events`: 下記構造、イベントの配列
  * `name`: 名前
    * `ja`: 日本語における表記
  * `twitter`: 主催者がイベント告知を行っているアカウントがあるなら、そのアカウントの数値形式のUser ID。任意。
  * `schedules`: 開催される日時。KnownScheduleを参照。

### KnownSchedule

配列。空ではない。`null`であることもない。

実情に応じて4種類のパターンがある。

1. 曜日などの周期的な相対指定により計算できる場合
    1. キャンセルや順延などがない→PeriodicScheduleのみの1要素配列
    2. キャンセルや順延などがある→SparsePeriodicScheduleとFixedScheduleの組み合わせ
2. 不定期だが、過去日・未来日が判明している場合→1要素以上のFixedSchedule
3. 不定期であり、過去日・未来日もわからない場合→UnknownScheduleのみの1要素配列

なお、3のパターンは要請があった場合にpermanentなプレースホルダとして設置される場合があることに注意。

### FixedSchedule

### PeriodicSchedule

### SparsePeriodicSchedule

### UnknownSchedule
