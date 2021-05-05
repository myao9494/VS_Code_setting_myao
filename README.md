# VS_Code_setting_myao

VS code のセットアップを纏めます

## extention をインストールする

- vsnotes
- Prettier - Code formatter
- markdownlint
- Markdown Checkbox
- Markdown Preview Enhanced
- Markdown All in One
- Bookmarks
- Git Graph
- python
- vscode-icons
- Japanese Language Pack for Visual Studio Code
- Rainbow CSV
- Draw.io Integration
- Edit csv
- Python Docstring Generator
- SandDance for VSCode
- Paste Image
- Markdown Extended

## 設定ファイル

1. 下記から設定を開き、右上のボタンから`settings.json`を開く（コマンドパレットからでもＯＫ）

   > ファイル　 → 　ユーザ設定　 → 　設定　 → 　ユーザ

1. 下記を実行の上、`settings.json`に貼り付けて保存

   - `"vsnotes.defaultNotePath":`に VS notes の保存フォルダパスを入れる

```json
{
  "window.zoomLevel": -1,
  "workbench.editor.enablePreview": false,
  "git.autofetch": true,
  "[markdown]": {
    // "editor.fontFamily": "Cambria, 游明朝",
    "editor.lineHeight": 24,
    "editor.fontSize": 14
  },
  "pasteImage.namePrefix": "${currentFileNameWithoutExt}_", // デフォルトのファイル名の頭にmarkdown名をつける
  "pasteImage.path": "${currentFileDir}/image/${currentFileNameWithoutExt}/", //(markdownファイルのディレクトリ内)/img内に画像を保存
  "pasteImage.prefix": "./", //pathの調整
  "pasteImage.showFilePathConfirmInputBox": true, // ペースト時にファイル名を変更する
  "pasteImage.filePathConfirmInputBoxMode": "onlyName",
  "vsnotes.defaultNotePath": "ここにパスを入れる",
  "vsnotes.noteTitleConvertSpaces": " ",
  "vsnotes.defaultNoteTitle": "{title}.{ext}",
  "vsnotes.tokens": [
    {
      "type": "title",
      "token": "{title}",
      "description": "Insert note title from input box.",
      "format": "Untitled"
    },
    {
      "type": "extension",
      "token": "{ext}",
      "description": "Insert file extension.",
      "format": "md"
    }
  ],
  "vsnotes.templates": ["base"],
  "markdown-preview-enhanced.enableExtendedTableSyntax": true,
  "markdown-preview-enhanced.enableScriptExecution": true,
  "markdown.preview.breaks": true,
  "markdown.extension.orderedList.marker": "one",
  "markdown.extension.orderedList.autoRenumber": false,
  "markdown.extension.syntax.decorations": false,
  "markdown.extension.tableFormatter.enabled": false,
  "markdown-preview-enhanced.codeBlockTheme": "dark.css",
  "markdown-preview-enhanced.revealjsTheme": "black.css",
  "markdown-preview-enhanced.previewTheme": "github-dark.css",
  "workbench.iconTheme": "vscode-icons",
  "[css]": {
    "editor.defaultFormatter": "aeschli.vscode-css-formatter"
  },
  "vscodeGoogleTranslate.preferredLanguage": "Japanese",
  "editor.formatOnSave": true
}
```

## VS notes のスニペットの登録

[Code]> [基本設定] > [ユーザースニペット] で、markdown.json を開き、下記を追加

```json
"vsnote_template_base": {
    "prefix": "vsnote_template_base",
    "body": [
        "---",
        "tags:",
        "\t- base",
        "---",
        "\n# $TM_FILENAME_BASE\n",
        "$1",
    ],
    "description": "base Template",
    }
```

## Markdown Preview Enhanced の設定

ctrl+shift+p を押し、 Markdown Preview Enhanced: Customize Css を開く
見出しの下線と番号を入れる（インストール後、一回プレビューをしないと、エラーになるので注意！）

```previwe.css
/* Please visit the URL below for more information: */
/*   https://shd101wyy.github.io/markdown-preview-enhanced/#/customize-css */

.markdown-preview.markdown-preview {
  // modify your style here
  // eg: background-color: blue;

  //   font-size: 12pt;

  table {
    font-size: 10pt;
    line-height: 1.2em;
    padding-left: 2em;
  }
  th {
    background-color: rgb(221, 221, 221);
    font-size: 10pt;
  }

  // codeブロック
  pre {
    margin-left: 1.5em;
  }

  ul li pre,
  ol li pre {
    margin-left: -1.5em;
  }

  // 引用
  blockquote {
    margin-left: 3em;
  }
  blockquote p {
    margin-left: -2.5em;
    font-size: 10pt;
  }
  blockquote blockquote {
    margin-left: 0.3em;
  }

  // mermaid
  .mermaid {
    margin-left: 1.5em;
  }

  // 箇条書きなど
  ul {
    margin-left: 2em;
    font-size: 12pt;
  }
  ul ul {
    margin-left: -1em;
    font-size: 12pt;
  }

  ol {
    margin-left: 1.7em;
    font-size: 12pt;
  }
  ol ol {
    margin-left: -1em;
    font-size: 12pt;
  }

  // イタリックと強調
  em {
    margin: 0 3px;
    padding: 0 5px;
    background: rgba(255, 192, 203, 0.3);
    font-weight: bold;
  }
  strong {
    background-color: #fff081;
    color: rgb(255, 0, 0);
    font-size: 15pt;
  }

  p {
    padding-left: 2em;
    font-size: 12pt;
    margin-bottom: 1pt;
  }
  li p {
    margin-left: -2.5em;
    font-size: 10pt;
  }
  body {
    counter-reset: chapter;
  }
  h1 {
    counter-reset: sub-chapter;
    font-size: 18pt;
    padding: 0.4em 0.5em; /*文字の上下 左右の余白*/
    color: #000000; /*文字色*/
    background: #ffec81; /*背景色*/
    border-left: solid 5px #90caff; /*左線*/
    border-bottom: solid 3px #000000; /*下線*/
  }
  h2 {
    counter-reset: section;
    font-size: 13pt;
    position: relative;
    padding: 0.6em;
    background: #ebffa3;
    color: rgb(0, 0, 0);
    margin-left: 0.2em;
    // border-top: solid 1px #000000; /*上線*/
    border-bottom: solid 1px #d2dd06; /*下線*/
  }
  h2::before {
    counter-increment: sub-chapter;
    content: counter(sub-chapter) ". ";
    padding-right: 0.2em;
  }
  h3 {
    counter-reset: sub-section;
    font-size: 13pt;
    position: relative;
    padding: 0.3em;
    padding-left: 1em;
    border-style: solid;
    border-width: 0 0 1px 0;
    // margin-left: 0.4m;
    // background: #4b8020;
    // color: rgb(0, 0, 0);
  }
  h3::before {
    counter-increment: section;
    content: counter(sub-chapter) "." counter(section) ". ";
    padding-right: 0.2em;
  }
  h4 {
    counter-reset: sub-sub-section;
    font-size: 12pt;
    padding-left: 1.2em;
    // margin-left: 0.6em;
    // color: white;
  }
  h4::before {
    counter-increment: sub-section;
    content: counter(sub-chapter) "." counter(section) "." counter(sub-section) ".";
    padding-right: 0.5em;
  }
  h5 {
    counter-reset: sub-sub-sub-section;
    font-size: 12pt;
    padding-left: 1.4em;
    // margin-left: 0.8em;
    // color: white;
  }
  h5::before {
    counter-increment: sub-sub-section;
    content: counter(sub-chapter) "." counter(section) "." counter(sub-section) "."
      counter(sub-sub-section) ".";
    padding-right: 0.5em;
  }
}
```
