# Microsoft Power BI

## 概要

本ノートはMicrosoft Power BIの研修にて各種情報共有で使用します。

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



■概要

[Power BI とは?](https://learn.microsoft.com/ja-jp/power-bi/fundamentals/power-bi-overview)

[Power BI サービス ビジネス ユーザー向けの基本的な概念](https://learn.microsoft.com/ja-jp/power-bi/consumer/end-user-basic-concepts)

■データの取り込み

[Power BI Desktop のデータ ソース](https://learn.microsoft.com/ja-jp/power-bi/connect-data/desktop-data-sources)

[ファイルから Power BI 用のデータを取得する](https://learn.microsoft.com/ja-jp/power-bi/connect-data/service-get-data-from-files)

[Power BI Desktop でストレージ モードを管理する](https://learn.microsoft.com/ja-jp/power-bi/transform-model/desktop-storage-mode)

[Power Query のクエリ評価とクエリ フォールディングの概要](https://learn.microsoft.com/ja-jp/power-query/query-folding-basics)

■データの加工

[Power BI Desktop でのデータ型](https://learn.microsoft.com/ja-jp/power-bi/connect-data/desktop-data-types)

※SharePointの取り込み内容からTagを取り除くための構文
（ColumnNameを任意の列名に変更してカスタム列を作成）

```Power Query M
let
startPos = Text.PositionOf([ColumnName], ">") + 1,
endPos = Text.PositionOf([ColumnName], "</div>"),
extractedText = Text.Middle([ColumnName],startPos, endPos - startPos)
in
extractedText
```

※単位を統一する構文（例ではメートルに統一）

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



■データモデリング

[Power BI Desktop でのモデル リレーションシップ](https://learn.microsoft.com/ja-jp/power-bi/transform-model/desktop-relationships-understand)

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

NETWORKDAYS（休日を外す（祝日非対応））

https://learn.microsoft.com/ja-jp/dax/networkdays-function-dax

※※日本の祝日は内閣府がCSVファイルにしてくれています。下記のリンクをソースとすることで祝日の日付を取り込むことが可能です

https://www8.cao.go.jp/chosei/shukujitsu/syukujitsu.csv

変数を使用して DAX の数式を改善する

https://learn.microsoft.com/ja-jp/dax/best-practices/dax-variables

Power BI Desktop の DirectQuery

https://learn.microsoft.com/ja-jp/power-bi/connect-data/desktop-use-directquery

■ビジュアライズ

Power BI での視覚化の種類

[https://learn.microsoft.com/ja-jp/power-bi/visuals/power-bi-visualization-types-for-reports-and-q-and-a](https://learn.microsoft.com/ja-jp/power-bi/visuals/power-bi-visualization-types-for-reports-and-q-and-a)

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

■Power BI Serviceとの連携

Power BI Desktop とPower BI サービスの違い：Power BIでレポート作成・分析を行うために必要なものは？

[https://jpbap-sqlbi.github.io/blog/powerbi/pbi_desktop_service/](https://jpbap-sqlbi.github.io/blog/powerbi/pbi_desktop_service/)

Power BI サービスのデータセット更新手順について

https://jpbap-sqlbi.github.io/blog/powerbi/pbi_refresh_settings/

Power BI ライセンスの違い（Free・Pro・Premium Per User・Premium Per Capacity・Embedded・Fabric）

https://jpbap-sqlbi.github.io/blog/powerbi/pbi_license/

※参考資料

https://pbifb.blob.core.windows.net/container/PBILicense_20250729.pdf

 

<details><summary>接続先情報</summary>

    ※不正利用防止のためURLを分割しています。共通項目の後にご自身の情報を繋げてURLとして入力してください
    Power BI入門 演習手順
    https://github.com/ctct-edu/Power-BI-for-beginners/tree/main/LabManual
    共通項目
    https://bst-64746a40-aab3-4b12-abfb-1afb2482426a.bastion.azure.com/api/shareable-url/
    個別項目
    usui		48c2d2ea-562e-42cf-93c8-b52b53033b88
    ou		73b768ea-c010-49c3-88bf-ab074f586b83
    onoda		555d5f1c-1dfc-469b-839e-cb17da667af6
    katsuma		3f5bcbc8-0c27-4085-8c5d-b779f6caf1ab
    kanazawa	301255bc-2385-4ebc-810a-8fcd85736830
    kamamasu	c0384c20-57d4-4faf-8361-51eef4dc5246
    kinoshita	768e75a4-f66c-4cdf-af52-c3ca30e48a6a
    kojima		ed0b7066-4c6a-4e99-bbe8-cd9fa0ef015d
    saruwatari	76fda53f-7e72-4b09-a6c4-89e4426771c6
    shibuya		15681145-0a13-47d7-afb3-e31c791eacb3
    sugishima	658bc90a-8e31-4661-be93-61073880a45f
    takano		44510f16-6868-4a72-8a4c-5fe9f097c0c9
    takahashi	36602ade-1f0a-4ce8-acd7-0b2c876cce5f
    taketomi	2a9dd2f8-7d21-486d-a187-530bdefd78ee
    tanaka		ea5d22e1-aeec-4f7d-b99d-89fbbb004065
    tamura		ec156481-9289-4761-bf4f-48c1bc92aab8
    nishimura	030ea045-c4b9-414d-81ce-e4747a4ebf47
    hiraishi	84012b99-6dbe-45e7-a358-421de6124cb9
    hiranaka	fdffcba4-5a14-45db-be6a-910223e69e89
    hirotaki	25947478-e3b4-455d-b7ce-bccd0a7ffe56
    futatsugi	5f2cf4d8-9503-4f4c-ba7f-7e9cf1eb148d
    hosoda		656f2c2e-95a8-4690-a0f0-06f5ff977a85
    muneyuki	1ace1def-7bc2-4a55-bd88-44b9db35cf3c

</details>

