# PL-300 Microsoft Power BI Data Analyst

## 概要

本ノートはPL-300 Microsoft Power BI Data Analystの研修にて各種情報共有で使用します。

> [!Note]
>
>  パブリックなリポジトリとなるため、本ノートを保存（ダウンロード）していただくことが可能です

## アカウント情報

### Skillableへの登録

下記のリンクから演習環境へのアクセス準備を開始してください。

[Preparation - 演習環境の使用開始](https://github.com/ctct-edu/Skillable/blob/main/Preparation.md)

なお、本研修で使用するトレーニングキーは以下の通りです。

| 連番          | トレーニングキー |
| ------------- | ---------------- |
| 中野（徳） 様 | 6B9EB8CE5C724611 |
| 杉﨑 様       | 2271614907EF448B |
| 中野（弘） 様 | 39CF30442C3B4573 |
| 大元 様       | A307F0A0B3F643F4 |
| 下村 様       | 4E3A6C14E54A4A1E |
| 小澤 様       | 70843ACF22F54FFB |
| 野本 様       | 61739A51E32A45EB |
| 宮本 様       | 183815AC58F24C78 |
| スー 様       | 66D6120843734770 |
| 國谷 様       | EC8FB040AEF14F46 |
| 武冨 様       | A1113B0CAE474BFA |
| 遠矢 様       | 372EE85932434A5F |
| 甲斐 様       | CA67873062854ABF |
| 上野 様       | B789ED5C780A464D |
| 笹井 様       | A16D190088A643A5 |
| 鍛 様         | E9539DA1D2B3483A |
| 稲葉 様       | 6134BB3687884471 |
| 今荘 様       | 3006CE3258B142E2 |
| ケイン 様     | AE0BCC1D5CEF4F32 |
| 江藤 様       | 7574512E53EF43AD |
| 横山 様       | C86E63AA2832444E |
| 佐藤 様       | 16DB64E52CED4F65 |



## 補足情報（各種ドキュメントリンク）

■Microsoft Learn - Power BI Data Analyst

https://learn.microsoft.com/ja-jp/training/courses/pl-300t00

■Microsoft公式Github ラボ関連情報

[PL-300-Microsoft-Power-BI-Data-Analyst.ja-jp](https://github.com/MicrosoftLearning/PL-300-Microsoft-Power-BI-Data-Analyst.ja-jp)

※ラボ手順のファイルは以下のフォルダにまとめられています

https://github.com/MicrosoftLearning/PL-300-Microsoft-Power-BI-Data-Analyst.ja-jp/tree/main/Instructions/Labs

### Module01

[Power BI とは?](https://learn.microsoft.com/ja-jp/power-bi/fundamentals/power-bi-overview)

[Power BI サービス ビジネス ユーザー向けの基本的な概念](https://learn.microsoft.com/ja-jp/power-bi/consumer/end-user-basic-concepts)

### Module02

[Power BI Desktop のデータ ソース](https://learn.microsoft.com/ja-jp/power-bi/connect-data/desktop-data-sources)

[ファイルから Power BI 用のデータを取得する](https://learn.microsoft.com/ja-jp/power-bi/connect-data/service-get-data-from-files)

[Power BI Desktop でストレージ モードを管理する](https://learn.microsoft.com/ja-jp/power-bi/transform-model/desktop-storage-mode)

[Power Query のクエリ評価とクエリ フォールディングの概要](https://learn.microsoft.com/ja-jp/power-query/query-folding-basics)

### Module03

[Power BI Desktop でのデータ型](https://learn.microsoft.com/ja-jp/power-bi/connect-data/desktop-data-types)

※質問いただいたSharePointの取り込み内容からTagを取り除くための構文
（ColumnNameを任意の列名に変更してカスタム列を作成）

```Power Query M
let
startPos = Text.PositionOf([ColumnName], ">") + 1,
endPos = Text.PositionOf([ColumnName], "</div>"),
extractedText = Text.Middle([ColumnName],startPos, endPos - startPos)
in
extractedText
```

### Module04

[Power BI Desktop でのモデル リレーションシップ](https://learn.microsoft.com/ja-jp/power-bi/transform-model/desktop-relationships-understand)

### Module05

[DAX 関数リファレンス](https://learn.microsoft.com/ja-jp/dax/dax-function-reference)

CALENDARAUTO
https://learn.microsoft.com/ja-jp/dax/calendarauto-function-dax
MEDIAN
https://learn.microsoft.com/ja-jp/dax/median-function-dax
DISTINCTCOUNT
https://learn.microsoft.com/ja-jp/dax/distinctcount-function-dax
COUNTROWS
https://learn.microsoft.com/ja-jp/dax/countrows-function-dax
HASONEVALUE
https://learn.microsoft.com/ja-jp/dax/hasonevalue-function-dax
DIVIDE
https://learn.microsoft.com/ja-jp/dax/divide-function-dax
ISINSCOPE
https://learn.microsoft.com/ja-jp/dax/isinscope-function-dax
