[![npm version](https://badge.fury.io/js/gulp-css-spriter.svg)](https://github.com/xiaopig123456/gulp-css-spriter-dookay) [![Build Status](https://travis-ci.org/MadLittleMods/gulp-css-spriter.svg?branch=master)](https://github.com/xiaopig123456/gulp-css-spriter-dookay)

# gulp-css-spriter-dookay

`gulp-css-spriter-dookay`，雪碧图处理插件。基于`gulp-css-spriter`插件进行了改良，新增配置项`matchReg`,用于是过滤需要合并的图片。

# Install

```
npm install gulp-css-spriter-dookay
```

# Usage
```js
var gulp = require('gulp');
var spriter = require('gulp-css-spriter-dookay');
var minifyCSS = require('gulp-minify-css'); // https://www.npmjs.com/package/gulp-minify-css

gulp.task('css', function() {
  return gulp.src('./src/css/styles.css')
    .pipe(spriter({
      spriteSheet: './dist/images/sprite.png',
        pathToSpriteSheetFromCSS: '../images/sprite.png',
        spritesmithOptions:{
          padding:10
        },
        matchReg:{
          pattern:"\.\./images\/icons\/"
        }
    }))
    .pipe(minifyCSS())
    .pipe(gulp.dest('./dist/css'));
});
```

# Options
- `matchReg`: object - 匹配规则
  - `pattern`: string 正则表达式，默认为null，表示全部背景图片
  - `attributes`: string 可选的字符串，包含属性 "g"、"i" 和 "m"，分别用于指定全局匹配、区分大小写的匹配和多行匹配
- 其他配置项请参考https://github.com/MadLittleMods/gulp-css-spriter
