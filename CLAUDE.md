# car-app リポジトリ 作業ルール

## 最初に必ず読むこと
- 作業を始める前に `shared_contract.md`(アプリ間の共通仕様書)を必ず読むこと。
- `shared_contract.md` は ciel-system リポジトリにも同じ内容のものがある。更新した場合は両方を同じ内容にそろえること。

## このリポジトリのアプリ
- `index.html`: car-app本体(在庫車両・代車・レンタカー管理)。共通仕様書では `carapp_index.html` と呼ばれているファイル。
- `check_migrate.html`, `fix_kana2.html`, `resize_images.html`: 補助ツール。指示がない限り編集しない。

## 共通データへの影響
- car-appは `stock` / `stockArchive` / `cars` ノードの主な書き込み元で、他のツール(ハブ・pricing・pricetag等)がこれらを読んでいる。
- これらのノードのフィールド名・形式を変える変更は、他のアプリに影響する。自分で実装せず、管理セッション(またはユーザー)に報告して判断を仰ぐ。
- `stock/{id}/vin` は正規化前の生の表記のまま保存する(`shared_contract.md` 3章)。

## 修正時のルール
- 修正のたびに、ファイル内のバージョン表記を+0.01する。
- 修正後はJSの構文チェックを行う(例: `<script>` 部分を抜き出して `node --check`)。
- コミットメッセージは日本語で「ファイル名 vX.XX: 変更内容」の形式にする(例: `index.html v1.93: 代車一覧の並び順を修正`)。

## GitHub
- リモート: `https://github.com/cielautoworks/car-app`(mainブランチ)
- mainへのマージとpushは、差分をユーザーに確認してもらってから行う。
