# api documentation for  [gulp-inline-css (v3.1.0)](https://github.com/jonkemp/gulp-inline-css#readme)  [![npm package](https://img.shields.io/npm/v/npmdoc-gulp-inline-css.svg?style=flat-square)](https://www.npmjs.org/package/npmdoc-gulp-inline-css) [![travis-ci.org build-status](https://api.travis-ci.org/npmdoc/node-npmdoc-gulp-inline-css.svg)](https://travis-ci.org/npmdoc/node-npmdoc-gulp-inline-css)
#### Inline linked css in an html file. Useful for emails.

[![NPM](https://nodei.co/npm/gulp-inline-css.png?downloads=true&downloadRank=true&stars=true)](https://www.npmjs.com/package/gulp-inline-css)

[![apidoc](https://npmdoc.github.io/node-npmdoc-gulp-inline-css/build/screenCapture.buildCi.browser.%252Ftmp%252Fbuild%252Fapidoc.html.png)](https://npmdoc.github.io/node-npmdoc-gulp-inline-css/build/apidoc.html)

![npmPackageListing](https://npmdoc.github.io/node-npmdoc-gulp-inline-css/build/screenCapture.npmPackageListing.svg)

![npmPackageDependencyTree](https://npmdoc.github.io/node-npmdoc-gulp-inline-css/build/screenCapture.npmPackageDependencyTree.svg)



# package.json

```json

{
    "author": {
        "name": "Jonathan Kemp",
        "url": "http://jonkemp.com/"
    },
    "bugs": {
        "url": "https://github.com/jonkemp/gulp-inline-css/issues"
    },
    "dependencies": {
        "gulp-util": "^3.0.0",
        "inline-css": "^2.2.1",
        "through2": "^0.6.1"
    },
    "description": "Inline linked css in an html file. Useful for emails.",
    "devDependencies": {
        "coveralls": "^2.11.6",
        "event-stream": "^3.3.2",
        "gulp": "^3.9.0",
        "gulp-eslint": "^1.1.1",
        "gulp-mocha": "^2.0.0",
        "mocha": "*",
        "nyc": "^5.0.0",
        "should": "^4.6.0"
    },
    "directories": {
        "test": "test"
    },
    "dist": {
        "shasum": "71d6dff2adae5ba241eaf568798ffbd3a9c8cf09",
        "tarball": "https://registry.npmjs.org/gulp-inline-css/-/gulp-inline-css-3.1.0.tgz"
    },
    "engines": {
        "node": ">=0.10.0"
    },
    "files": [
        "index.js"
    ],
    "gitHead": "b42157d3079f4ad0021907495a0ba68c8e54b557",
    "homepage": "https://github.com/jonkemp/gulp-inline-css#readme",
    "keywords": [
        "gulpplugin",
        "inline",
        "css",
        "html",
        "email"
    ],
    "license": "MIT",
    "main": "index.js",
    "maintainers": [
        {
            "name": "jonkemp"
        }
    ],
    "name": "gulp-inline-css",
    "optionalDependencies": {},
    "repository": {
        "type": "git",
        "url": "git+https://github.com/jonkemp/gulp-inline-css.git"
    },
    "scripts": {
        "coverage": "nyc npm test && nyc report",
        "coveralls": "nyc npm test && nyc report --reporter=text-lcov | coveralls",
        "lint": "gulp lint",
        "test": "mocha"
    },
    "version": "3.1.0"
}
```



# <a name="apidoc.tableOfContents"></a>[table of contents](#apidoc.tableOfContents)

#### [module gulp-inline-css](#apidoc.module.gulp-inline-css)
1.  [function <span class="apidocSignatureSpan"></span>gulp-inline-css (opt)](#apidoc.element.gulp-inline-css.gulp-inline-css)
1.  [function <span class="apidocSignatureSpan">gulp-inline-css.</span>toString ()](#apidoc.element.gulp-inline-css.toString)



# <a name="apidoc.module.gulp-inline-css"></a>[module gulp-inline-css](#apidoc.module.gulp-inline-css)

#### <a name="apidoc.element.gulp-inline-css.gulp-inline-css"></a>[function <span class="apidocSignatureSpan"></span>gulp-inline-css (opt)](#apidoc.element.gulp-inline-css.gulp-inline-css)
- description and source-code
```javascript
gulp-inline-css = function (opt) {
    return through.obj(function (file, enc, cb) {
        var self = this,
            _opt = JSON.parse(JSON.stringify(opt || {}));

        // 'url' option is required
        // set it automatically if not provided
        if (!_opt.url) {
            _opt.url = 'file://' + file.path;
        }

        if (file.isNull()) {
            cb(null, file);
            return;
        }

        if (file.isStream()) {
            cb(new gutil.PluginError('gulp-inline-css', 'Streaming not supported'));
            return;
        }

        inlineCss(file.contents, _opt)
            .then(function (html) {
                file.contents = new Buffer(String(html));

                self.push(file);

                return cb();
            })
            .catch(function (err) {
                if (err) {
                    self.emit('error', new gutil.PluginError('gulp-inline-css', err));
                }
            });
    });
}
```
- example usage
```shell
n/a
```

#### <a name="apidoc.element.gulp-inline-css.toString"></a>[function <span class="apidocSignatureSpan">gulp-inline-css.</span>toString ()](#apidoc.element.gulp-inline-css.toString)
- description and source-code
```javascript
toString = function () {
    return toString;
}
```
- example usage
```shell
n/a
```



# misc
- this document was created with [utility2](https://github.com/kaizhu256/node-utility2)
