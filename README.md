# ID Photo Print

**ID Photo Print** is a lightweight, browser-based tool for preparing and printing ID photos at specified physical dimensions. It lets you crop, straighten, retouch and arrange photos on a sheet, then print directly from Google Chrome—without exporting a PDF.

**ID Photo Print** は、スマートフォンなどで撮影した写真を証明写真サイズにトリミング・補正し、指定寸法で用紙へ配置して **Chromeから直接印刷**するアプリです。PDFへの書き出しは必要ありません。

- **Version:** 1.0.0
- **License:** MIT — Copyright (c) 2026 cityedge
- **Primary target:** Google Chrome on Windows, with a supported printer
- **Distribution:** Standalone `index.html` / static GitHub Pages site
- **Languages:** 日本語 / English

## Features / 主な機能

| 機能 | 内容 |
| --- | --- |
| 写真の取り込み | JPG / PNG / WebP / BMP、ドラッグ＆ドロップ対応（最大100MB） |
| トリミング | ドラッグによる位置調整、100〜350%の拡大 |
| 回転 | 左右90°、傾き補正 −15〜+15° |
| 画質補正 | 明るさ（中間調）・コントラスト・色温度・シャープネス |
| 写真サイズ | 30×40、35×45、25×30、40×50、50×50mm、および自由指定 |
| 用紙サイズ | L判、2L判、はがき、A4、および自由指定、縦横切替 |
| レイアウト | 自動配置（上限4/9/16枚/無制限）、手動枚数、中央/上中央/左上 |
| 切り取りガイド | 四隅のトンボ、枠線、なし |
| 印刷 | 出力写真を600dpi相当で生成し、mm指定のSVGをChromeの印刷画面へ渡す |
| 設定保存 | 用紙・配置・言語・表示タブを自動保存。最後に編集した写真は同じファイルを再選択したときに編集値を復元 |

用紙の余白の**初期値は12mm**、写真の間隔の初期値は3mmです。印刷倍率はChromeの印刷画面で**100%**にしてください。

## Quick start / 使い始める

1. このリポジトリの `index.html` をChromeで開きます。GitHub Pagesを有効にしている場合は公開URLからも利用できます。
2. 「写真・回転」タブで写真を読み込み、写真サイズ・向き・トリミングを調整します。
3. 必要なら「画質補正」タブで明るさ・色温度などを変更します。
4. 「用紙・配置」タブで用紙・枚数・余白・配置位置を設定します。
5. 用紙プレビューを確認し、画面上部の「Chromeから直接印刷」を押します。
6. Chromeの印刷画面で、**用紙サイズを合わせる／倍率100%／余白なし／ヘッダーとフッターなし**を確認します。プリンタードライバー側のフチなし拡大もオフにしてください。

詳しい使い方は [ユーザーマニュアル（日本語）](USER_MANUAL.md) / [User Manual (English)](USER_MANUAL_EN.md) を参照してください。

## GitHub Pages で公開する

ビルド処理もサーバー側プログラムも不要です。リポジトリ直下に `index.html` と同梱のドキュメントを置き、GitHubの **Settings → Pages → Build and deployment** で **Deploy from a branch / main / (root)** を選択してください。

詳細：[GitHub公開手順](RELEASE_GUIDE.md) / [GitHub Pages公式ドキュメント](https://docs.github.com/en/pages/getting-started-with-github-pages/creating-a-github-pages-site)

**注意：** ZIPファイルをそのままリポジトリにアップロードしてもGitHub Pagesのトップページにはなりません。ZIPを展開し、中身の `index.html` をリポジトリのルートへ配置してください。

## Settings and privacy / 設定保存・プライバシー

- すべての画像処理は端末上のブラウザ内で実行され、画像を外部サーバーへアップロードしません。外部API・外部JavaScriptライブラリも使用しません。
- `localStorage` に用紙・レイアウト・言語・選択タブの設定を保存します。
- 最後に編集した**1枚の写真**について、ファイル属性から計算した識別子とトリミング・回転・画質補正の設定を保存します。再び同じ写真を選択すると編集値が戻ります。別の写真を選ぶと写真固有の編集値は初期化されます。
- **写真ファイル本体や画像の画素データは保存しません。** ページを開き直した際は写真を再度選択してください。
- 保存データは利用するサイト／ブラウザごとに分離されます。プライベートブラウジングや閲覧データ消去では消失します。ローカルの `file://` URLに対する保存動作はブラウザやファイルの場所に左右されるため、継続利用には固定のGitHub Pages URLを推奨します。
- ストレージが利用できない場合は画面下部に警告を表示します。写真の印刷機能は引き続き使用可能です。

## Requirements, limitations and accuracy / 対応条件と制限

- Windows版Google Chromeを主な検証対象としています。スマートフォン版・他ブラウザ・すべてのプリンターでの動作は保証しません。
- 印刷寸法はアプリがmm単位で指定しますが、最終的な精度はChromeの印刷設定とプリンタードライバー、プリンター本体に依存します。必要に応じてテスト印刷を行ってください。
- 写真を高解像度で作成しても、元画像の解像度が低い場合にディテールが増えるわけではありません。非常に大きなカスタムサイズでは画像メモリ保護のため600dpi相当より小さくなる場合があります。
- HEIC、TIFF、RAW形式や複数写真を一枚の用紙に混在させる機能、顔認識、背景の自動除去、プリンタードライバーの自動設定には対応しません。
- パスポート・各種申請書などは、寸法だけでなく背景、顔の比率、表情、画像補正の制限が設けられている場合があります。提出先の最新の規定を確認してください。

## Files / ファイル構成

```text
index.html          アプリ本体（単一HTML）
README.md           プロジェクト概要
USER_MANUAL.md      ユーザーマニュアル（日本語）
USER_MANUAL_EN.md   User manual (English)
RELEASE_GUIDE.md    GitHub公開・更新ガイド
CHANGELOG.md        更新履歴
LICENSE             MIT License
.nojekyll           GitHub PagesでJekyll処理を無効化するための空ファイル
```

## License / ライセンス

MIT License. See [LICENSE](LICENSE). Copyright (c) 2026 cityedge.
