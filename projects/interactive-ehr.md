# Interactive EHRで示すAIの実装と画面設計

診療タスクに合わせて電子カルテの情報を取得・表示し、利用者の要求から画面表示までの対応を確かめる研究用プロトタイプです。[公開リポジトリ](https://github.com/50m-regent/interactive-ehr)で実装を確認できます。

## 解決したい課題

診療で確認したい情報は、目的や作業によって変わります。固定された電子カルテ画面では、必要な情報を探し、複数の画面を行き来して確認する作業が生じます。

生成AIで専用の画面を作る場合にも、表示できたことだけでは要求を満たしたと判断できません。直近24時間の検査結果を求めても、SQLから期間条件が抜ければ、対象外の情報が含まれる可能性があります。

## 開発した仕組み

診療場面、タスク、表示部品、取得データをグラフとして表現し、画面に必要な情報と取得方法を結び付けます。画面構成はJSONで保持し、Geminiによる生成・編集と、Streamlitによる表示につなげています。

データ取得には読み取り専用SQLを使います。質問、SQL、取得結果、表示の対応を検査し、問題箇所の特定や修正を評価できる仕組みも開発しています。

主な技術は Python、Gemini、Streamlit、Pydantic、SQL、SQLGlot です。

## 確認できたこと

試作システムでは、用意したシナリオに沿った画面表示までを確認しています。技術評価では、条件を固定して作成した不整合を対象に、検査方法を比較しています。

現時点では、臨床での安全性や使いやすさ、作業時間の改善を実証したシステムとしては紹介しません。利用者による評価と実運用の検証は今後の課題です。

## 個人で取り組んだこと

個人制作として、システムの設計と実装、画面構成、生成結果を検査する評価の仕組みに取り組んでいます。

## 今後の評価

利用者による評価では、要求と画面の対応をどのように確認できるか、問題を見つけて修正できるかを検討します。実際の診療での利用については、別途検証が必要です。

## In English

Interactive EHR is my individual research prototype for generating electronic health record interfaces according to clinical tasks. It uses Gemini to produce a graph-based JSON specification, read-only SQL to retrieve data, and Streamlit to render the interface.

The research examines how to check the relationships between user requests, SQL, results, and presentation. A successfully rendered screen may still contain incorrect data when a time constraint is missing. Technical evaluation uses controlled synthetic inconsistencies; clinical safety, usability, and efficiency improvements have not yet been established.
