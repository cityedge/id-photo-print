# ID Photo Print v1.0.0 — GitHub公開・更新手順

このパッケージは、**単一HTMLアプリをGitHub Pagesで公開する**ことを想定しています。Node.js・ビルド・GitHub Actionsの独自設定・サーバー環境は必要ありません。

## 1. 配布ファイルの確認

展開したフォルダは次の構成です。

```text
ID-Photo-Print-v1.0.0/
  index.html
  README.md
  USER_MANUAL.md
  USER_MANUAL_EN.md
  RELEASE_GUIDE.md
  CHANGELOG.md
  LICENSE
  .nojekyll
```

`index.html` はアプリの起動ファイルです。`LICENSE` は指定されたMITライセンス原本で、Copyright (c) 2026 cityedge と記載されています。

**ZIPファイルだけをGitHubに配置してもサイトは公開できません。** 展開して中のファイルをリポジトリへアップロードしてください。

## 2. GitHubへ手動アップロードする

1. GitHubで新しいリポジトリを作成するか、既存のアプリ用リポジトリを開きます。公開するならリポジトリをPublicにします。
2. リポジトリの **Add file → Upload files** から、パッケージ内のファイルをルートへアップロードします。`.nojekyll` は不可視ファイルなので、手動アップロード時に見落とさないよう確認してください（このアプリ単体なら省略しても通常動作します）。
3. `index.html` が**リポジトリ直下**にあり、`LICENSE` とドキュメントが同じ階層にあることを確認します。
4. コミットメッセージの例：`Release ID Photo Print v1.0.0`。

README内の相対リンクは、このファイル構成のままで機能します。

## 3. GitHub Pagesを有効化する

1. リポジトリの **Settings** を開きます。
2. 左メニューの **Pages** を選びます。
3. **Build and deployment → Source:** `Deploy from a branch`。
4. **Branch:** `main`、フォルダは **`/ (root)`** を選択して保存します（既存リポジトリの既定ブランチが異なる場合は適宜変更）。
5. 公開されたURLから、`ID Photo Print` の画面が表示されるか確認します。

一般的なプロジェクト用URLは `https://<GitHubユーザー名>.github.io/<リポジトリ名>/` です。ユーザーページ用リポジトリを用いる場合はパスが異なります。

GitHub公式手順：<https://docs.github.com/en/pages/getting-started-with-github-pages/creating-a-github-pages-site>

## 4. 公開前の確認リスト

- [ ] ヘッダーが **ID Photo Print / v1.0.0**（日本語タイトル、Browser-only、MVPの表示が残っていない）。
- [ ] 初回起動で「用紙の余白」が**12mm**。
- [ ] JPGまたはPNGを読み込み、中央のトリミングと右の用紙プレビューに反映できる。
- [ ] 回転／傾き／4種の補正が動く。
- [ ] 自動配置の上限4/9/16/無制限が動作する。
- [ ] 配置位置「中央／上中央／左上」が用紙プレビューに反映される。
- [ ] 保存した用紙・配置・言語・タブ設定が再読込後も残る。
- [ ] 写真本体は自動復元されず、同じ写真を再選択すると編集値が戻る。
- [ ] Chromeの印刷画面で意図した用紙サイズ・向きになり、1ページに出力される。
- [ ] 実機で寸法・切り取り位置を確認する（推奨）。
- [ ] `README.md` と `USER_MANUAL.md` がGitHub上で読める。
- [ ] `LICENSE` が存在し、指定の著作権者が記載されている。

## 5. リリース登録（任意）

GitHubの **Releases** から `v1.0.0` のタグを作り、配布用ZIPを添付できます。説明文には、直接印刷・600dpi固定・用紙余白12mm・設定保存・MITライセンスを記載するとよいでしょう。

リリースZIPは配布物です。GitHub Pagesで使うアプリ本体は、常にリポジトリ内の `index.html` です。

## 6. 今後の更新と設定保存の注意

GitHub Pagesでは、**同じURLで `index.html` を更新**してください。そうするとブラウザの保存設定を継続利用しやすくなります。別のリポジトリやURLへ移動した場合、設定は通常引き継がれません。

ローカルでHTMLを直接開く場合、Chromeの `file://` URLに対する `localStorage` の扱いはブラウザ依存です。ファイル名を毎回変える配布形式より、同じ場所に `index.html` を置くかGitHub PagesのURLを使う運用が適しています。

v0.3.2からは主要な用紙設定を移行できます。ただし旧版の余白初期値6mmはv1.0.0で12mmへ更新します。

## 7. ライセンス

MIT License、Copyright (c) 2026 cityedge。`LICENSE` の全文を削除・改変せず、再配布時も同梱してください。
