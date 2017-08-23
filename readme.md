## gulp-query-rollup
Webpack plugin for [gulp-query](https://github.com/gulp-query/gulp-query)

Uses
[rollup-plugin-buble](https://www.npmjs.com/package/rollup-plugin-buble),
[rollup-plugin-uglify](https://www.npmjs.com/package/rollup-plugin-uglify) with [uglify-es](https://www.npmjs.com/package/uglify-es),
[rollup-plugin-node-resolve](https://www.npmjs.com/package/rollup-plugin-node-resolve) and
[rollup-plugin-commonjs](https://www.npmjs.com/package/rollup-plugin-commonjs)

Rollup is a module bundler for JavaScript which compiles small pieces of code into something larger and more complex, such as a library or application

```
npm install gulp-query gulp-query-rollup
```

### Example
Paste the code into your `gulpfile.js` and configure it
```javascript
let build = require('gulp-query')
  , rollup = require('gulp-query-rollup')
;
build((query) => {
    query.plugins([rollup])
      // Create module App
      .rollup('src/js/app.js','js/','app')
    
      // Rename and create module Undercover
      .rollup('src/js/admin.js','js/undercover.js')
    
      // Config as object
      .rollup({
        from: 'src/js/main.js',
        to: 'js/',
        name: 'main',
        moduleName: 'Main'
      })
    ;
});
```
And feel the freedom
```
gulp
gulp --production // For production
gulp watch // Watching change
gulp rollup // Only for webpack
gulp rollup:app // Only for app.js
gulp rollup:admin rollup:main watch // Watching change only for admin.js (admin/**/*) and main.js (main/**/*)
...
```

### Options
```javascript
.rollup({
    name: "task_name", // For gulp rollup:task_name 
    moduleName: "moduleName", // Rollup is a module bundler 
    format: "iife", // Default: iife -- amd, cjs, es, umd 
    from: "src/js/app.js",
    to: "js/", // set filename "js/concat.js" -- for rename
    source_map: true,
    source_map_type: 'inline',
    full: false // if set true is without compress in prod
})
```