# PL-300 Microsoft Power BI Data Analyst

## 概要

本ノートはPL-300 Microsoft Power BI Data Analystの研修にて各種情報共有で使用します。

> [!Note]
>
>  パブリックなリポジトリとなるため、本ノートを保存（ダウンロード）していただくことが可能です

## 補足情報（各種ドキュメントリンク）

■Microsoft Learn - Power BI Data Analyst

https://learn.microsoft.com/ja-jp/training/courses/pl-300t00

■Microsoft公式Github ラボ関連情報

[PL-300-Microsoft-Power-BI-Data-Analyst.ja-jp](https://github.com/MicrosoftLearning/PL-300-Microsoft-Power-BI-Data-Analyst.ja-jp)

※ラボ手順のファイルは以下のフォルダにまとめられています

https://github.com/MicrosoftLearning/PL-300-Microsoft-Power-BI-Data-Analyst.ja-jp/tree/main/Instructions/Labs

■Power BI Desktopの言語変更について

Power BI Desktopが英語で起動している場合は、[File] > [Options and settings] > [Options]の順に選択し、Optionsウィンドウで[GLOBAL]-[Regional Settings]に表示されるApplication languageとModel languageのドロップダウンリストからそれぞれ"Japanese(Japan)"を選択してアプリを再起動することで日本語に変更可能です。



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

※質問いただいた単位を統一する構文（例ではメートルに統一）

IFやSWITCHで条件に合致するかの判定と計算をさせる列を新たに構成しています

```
統一値 (Unified Value) = 
    SWITCH(
        TRUE(),
        Table[単位] = "m", Table[数値],                   -- メートルはそのまま
        Table[単位] = "cm", Table[数値] / 100,           -- センチメートルはメートルに変換
        Table[単位] = "mm", Table[数値] / 1000,          -- ミリメートルはメートルに変換
        Table[単位] = "km", Table[数値] * 1000,          -- キロメートルはメートルに変換
        Table[単位] = "yd", Table[数値] * 0.9144,        -- ヤードはメートルに変換
        Table[単位] = "ft", Table[数値] * 0.3048,        -- フィートはメートルに変換
        Table[単位] = "in", Table[数値] * 0.0254,        -- インチはメートルに変換
        Table[単位] = "mi", Table[数値] * 1609.34,       -- マイルはメートルに変換
        BLANK()                                          -- 該当しない場合は空欄
    )

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

※質問いただいていた関数

NETWORKDAYS（休日を外す（祝日非対応））

https://learn.microsoft.com/ja-jp/dax/networkdays-function-dax

※※日本の祝日は内閣府がCSVファイルにしてくれています。下記のリンクをソースとすることで祝日の日付を取り込むことが可能です

https://www8.cao.go.jp/chosei/shukujitsu/syukujitsu.csv

### Module06

変数を使用して DAX の数式を改善する

https://learn.microsoft.com/ja-jp/dax/best-practices/dax-variables

Power BI Desktop の DirectQuery

https://learn.microsoft.com/ja-jp/power-bi/connect-data/desktop-use-directquery

### Module07

Microsoft AppSource

https://appsource.microsoft.com/ja-jp/marketplace/apps?product=power-bi-visuals

レポートでの書式設定に関するヒントとコツ
https://learn.microsoft.com/ja-jp/power-bi/visuals/service-tips-and-tricks-for-color-formatting?tabs=powerbi-desktop

Power BI のレポート内でビジュアルがどのように相互作用するか

https://learn.microsoft.com/ja-jp/power-bi/consumer/end-user-interactions

ページ ナビゲーターとブックマーク ナビゲーターを作成する

https://learn.microsoft.com/ja-jp/power-bi/create-reports/button-navigators?tabs=powerbi-desktop

Power BI レポートでドリルスルーを設定する

https://learn.microsoft.com/ja-jp/power-bi/create-reports/desktop-drillthrough

### Module09

Power BI サービスのデータセット更新手順について

https://jpbap-sqlbi.github.io/blog/powerbi/pbi_refresh_settings/

### Module10

Power BI ライセンスの違い（Free・Pro・Premium Per User・Premium Per Capacity・Embedded・Fabric）

https://jpbap-sqlbi.github.io/blog/powerbi/pbi_license/
