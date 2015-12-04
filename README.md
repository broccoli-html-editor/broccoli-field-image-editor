# broccoli-field-image-editor

_broccoli-field-image-editor_ は、 _broccoli-html-editor_ に カスタムフィールド "画像編集フィールド" を追加する拡張パッケージです。

※ モジュール化手順
下リンクの差分箇所を修正します  
https://goo.gl/aOB8Jn

※ 設定手順
### broccoli-field-image-editor install
- youngcorn/package.jsonに一行追加
```
"dependencies": {
  "broccoli-field-image-editor": "git://github.com/pickles2/broccoli-field-image-editor.git",
}
```
- npmモジュールダウンロード
```
# cd youngcorn
# npm i
```

- gulpfile.jsにタスクを追加
```
# atom gulpfile.js
```
```js
// broccoli-client (frontend) を処理
gulp.src(["node_modules/broccoli-field-image-editor/dist/**/*"])
  .pipe(gulp.dest("./dist/{PATH_TO_YOUR_DIRECTORY}"))
;
```

- baskendJSに追加  
```
# atom backend/apis/broccoliBridgeForThemeEditor.js
```
```js
'customFields': {
  'image-editor': require('broccoli-field-image-editor')
},
```

- frontendJSに追加  
```
# atom  src/project/themeEditor/editors/broccoli-html-editor/index.html.twig
```
```js
<!--broccoli-field-image-editor -->
<script src="/{PATH_TO_YOUR_DIRECTORY}broccoli-field-image-editor.js"></script>
<link rel="stylesheet" href="/{PATH_TO_YOUR_DIRECTORY}css/Jcrop.css" />
<script src="/{PATH_TO_YOUR_DIRECTORY}js/Jcrop-editor.js"></script>
<script src="/{PATH_TO_YOUR_DIRECTORY}js/Jcrop.js"></script>
<script src="/{PATH_TO_YOUR_DIRECTORY}js/jquery.animate-colors-min.js"></script>
<script src="/{PATH_TO_YOUR_DIRECTORY}js/rgbcolor.js"></script>
<script src="/{PATH_TO_YOUR_DIRECTORY}js/underscore-min.js"></script>

```

- themeに追加  
```
# atom src/project/themeEditor/editors/broccoli-html-editor/index_files/cont.js
```
```js
'customFields': {
  'image-editor': window.BroccoliFieldImageEditor
},
```

- templateを追加
```
# cp node_modules/broccoli-field-image-editor/tests/testdata/modules1/dev/image-editor {PATH_TO_YOUR_PROJECT_DIRECTORY}/px-files/themes/broccoli/modules/images/
```

- 配置&実行
```
# gulp; gulp watch;
```

## ライセンス - License

MIT License


## 作者 - Author

- (C)Misaki Shibata <misaki.pink@gmail.com>
