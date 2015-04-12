## gulp vs grunt

```javascript
var gulp = require('gulp');
var spawn = require('child_process').spawn;
var jeditor = require("gulp-json-editor");
var merge = require('merge-stream');

gulp.task('batch', function () {
  var pkgs = ['a', 'b'];
  var tasks = pkgs.map(function (pkg) {
    return gulp.src("./template/package.json")
      .pipe(jeditor({
        name: pkg
      }))
      .pipe(gulp.dest(pkg));
  });
  return merge(tasks);
});

gulp.task('npm', function (done) {
  spawn('npm', ['publish', ['template']], {
    stdio: 'inherit'
  }).on('close', done);
});
```