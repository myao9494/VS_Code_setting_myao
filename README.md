# VS_Code_setting_myao

VS code のセットアップを纏めます

## extentionをインストールする

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
- Excel to Markdown table
- Paste Image
- python Docstring Generator
- SandDance for VSCode
- Edit csv
- vscode-icons

## 設定ファイル

1. 下記から設定を開き、右上のボタンから`settings.json`を開く（コマンドパレットからでもＯＫ）

   > ファイル　 → 　ユーザ設定　 → 　設定　 → 　ユーザ

1. 下記を実行の上、`settings.json`に貼り付けて保存

   - `"vsnotes.defaultNotePath":`に VS notes の保存フォルダパスを入れる

```json
{
  "window.zoomLevel": -1,
  "workbench.editor.enablePreview": false, // ファイルを開いた時にタブが上書きされる問題を回避
  "git.autofetch": true,
  "terminal.integrated.shell.windows": "C:\\Windows\\System32\\cmd.exe",
  "vsnotes.defaultNotePath": "ここにパスを入れる",
  "vsnotes.noteTitleConvertSpaces": " ",
  "vsnotes.defaultNoteTitle": "{dt} {title}.{ext}",
  "vsnotes.tokens": [
    {
      "type": "datetime",
      "token": "{dt}",
      "format": "YYYY-MM-DD",
      "description": "Insert formatted datetime."
    },
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
  "markdown-preview-enhanced.previewTheme": "github-dark.css"
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

```css
/* Please visit the URL below for more information: */
/*   https://shd101wyy.github.io/markdown-preview-enhanced/#/customize-css */

.markdown-preview.markdown-preview {
  // modify your style here
  // eg: background-color: blue;

  font-size: 12pt;
  table {
    font-size: 10pt;
    line-height: 1.2em;
  }
  th {
    background-color: #222;
    font-size: 10pt;
  }
  a {
    font-size: 10pt;
    color: rgb(199, 228, 235);
    line-height: 1.8em;
  }
  p,
  ul,
  ol,
  li {
    font-size: 10pt;
    color: rgb(255, 255, 255);
    line-height: 1.8em;
  }
  p {
    padding-left: 1em;
  }

  body {
    counter-reset: chapter;
  }
  h1 {
    counter-reset: sub-chapter;
    font-size: 15pt;
    padding: 0.4em 0.5em; /*文字の上下 左右の余白*/
    color: #000000; /*文字色*/
    background: #3780df; /*背景色*/
    border-left: solid 5px #7db4e6; /*左線*/
    border-bottom: solid 3px #d7d7d7; /*下線*/
  }
  h2 {
    counter-reset: section;
    font-size: 14pt;
    position: relative;
    padding: 0.4em;
    background: #c5c5c5;
    color: rgb(0, 0, 0);
  }
  h2::before {
    counter-increment: sub-chapter;
    content: counter(sub-chapter) ". ";
  }
  h3 {
    counter-reset: sub-section;
    font-size: 13pt;
    position: relative;
    padding: 0.3em;
    background: #a72a2a;
    color: rgb(0, 0, 0);
  }
  h3::before {
    counter-increment: section;
    content: counter(sub-chapter) "." counter(section) ". ";
  }
  h4 {
    counter-reset: sub-sub-section;
    font-size: 12pt;
    color: white;
  }
  h4::before {
    counter-increment: sub-section;
    content: counter(sub-chapter) "." counter(section) "." counter(sub-section)
      ".";
  }
  h5 {
    counter-reset: sub-sub-sub-section;
    font-size: 12pt;
    color: white;
  }
  h5::before {
    counter-increment: sub-sub-section;
    content: counter(sub-chapter) "." counter(section) "." counter(sub-section)
      "." counter(sub-sub-section) ".";
  }
}

```
