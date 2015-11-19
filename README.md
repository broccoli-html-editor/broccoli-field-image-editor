# broccoli-imageeditor-field

_broccoli-imageeditor-field_ は、 _broccoli-html-editor_ に カスタムフィールド "画像編集フィールド" を追加する拡張パッケージです。

## インストール - Install

```
$ npm install broccoli-html-editor --save
$ npm install broccoli-imageeditor-field --save
```

※ モジュール化手順
下リンクの差分箇所を修正します  
https://goo.gl/oRQ9Lo

※ 設定手順
# broccoli-html-editor
https://github.com/tomk79/broccoli

### broccoli-imageeditor-field install
- youngcorn/package.jsonに一行追加
```
"dependencies": {
  "broccoli-imageeditor-field": "git://github.com/m-prj/broccoli-imageeditor-field.git",
}
```
- npmモジュールダウンロード
```
# cd youngcorn
# npm i
```

- gulpfile.jsにタスクを追加
```js
// broccoli-client (frontend) を処理
gulp.task("broccoli-client", function() {
	gulp.src(["node_modules/broccoli-imageeditor-field/dist/*"])
		.pipe(gulp.dest( './dist/libs/broccoli-imageeditor-field/dist/' ))
	;
```

- baskendJSに追加
-- backend/apis/broccoliBridgeForThemeEditor.js
```js
'customFields': {
  'imageeditor': require('broccoli-imageeditor-field')
```

- frontendJSに追加
-- src/project/themeEditor/editors/broccoli-html-editor/index.html.twig
```js
<!--broccoli-imageeditor-field -->
<script src="/libs/broccoli-imageeditor-field/dist/broccoli-imageeditor-field.js"></script>
```

- themeに追加
-- src/project/themeEditor/editors/broccoli-html-editor/index_files/cont.js
```js
'customFields': {
  'imageeditor': window.BroccoliImgEditField
},
```

- templateを追加
-- /marble/px-files/themes/broccoli/modules/images/
```sh
cp ~/broccoli-img-editor-field/tests/testdata/modules1/dev/imageeditor ~/marble/px-files/themes/broccoli/modules/images/
```


## ライセンス - License

MIT License


## 作者 - Author

- (C)Misaki Shibata <misaki.pink@gmail.com>

