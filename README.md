# test coverage for  [keypress (v0.2.1)](https://github.com/TooTallNate/keypress#readme)  [![npm package](https://img.shields.io/npm/v/npmtest-keypress.svg?style=flat-square)](https://www.npmjs.org/package/npmtest-keypress) [![travis-ci.org build-status](https://api.travis-ci.org/npmtest/node-npmtest-keypress.svg)](https://travis-ci.org/npmtest/node-npmtest-keypress)
#### Make any Node ReadableStream emit "keypress" events

[![NPM](https://nodei.co/npm/keypress.png?downloads=true)](https://www.npmjs.com/package/keypress)

| git-branch : | [alpha](https://github.com/npmtest/node-npmtest-keypress/tree/alpha)|
|--:|:--|
| coverage : | [![istanbul-coverage](https://npmtest.github.io/node-npmtest-keypress/build/coverage.badge.svg)](https://npmtest.github.io/node-npmtest-keypress/build/coverage.html/index.html)|
| test-report : | [![test-report](https://npmtest.github.io/node-npmtest-keypress/build/test-report.badge.svg)](https://npmtest.github.io/node-npmtest-keypress/build/test-report.html)|
| build-artifacts : | [![build-artifacts](https://npmtest.github.io/node-npmtest-keypress/glyphicons_144_folder_open.png)](https://github.com/npmtest/node-npmtest-keypress/tree/gh-pages/build)|

[![istanbul-coverage](https://npmtest.github.io/node-npmtest-keypress/build/screenCapture.buildCustomOrg.browser.coverage.html.png)](https://npmtest.github.io/node-npmtest-keypress/build/coverage.html/index.html)

[![test-report](https://npmtest.github.io/node-npmtest-keypress/build/screenCapture.buildCustomOrg.browser.%252Fhome%252Ftravis%252Fbuild%252Fnpmtest%252Fnode-npmtest-keypress%252Ftmp%252Fbuild%252Ftest-report.html.png)](https://npmtest.github.io/node-npmtest-keypress/build/test-report.html)

[![apidoc](https://npmdoc.github.io/node-npmdoc-keypress/build/screenCapture.buildApidoc.browser.%252Fhome%252Ftravis%252Fbuild%252Fnpmdoc%252Fnode-npmdoc-keypress%252Ftmp%252Fbuild%252Fapidoc.html.png)](https://npmdoc.github.io/node-npmdoc-keypress/build/apidoc.html)

![npmPackageListing](https://npmtest.github.io/node-npmtest-keypress/build/screenCapture.npmPackageListing.svg)

![npmPackageDependencyTree](https://npmtest.github.io/node-npmtest-keypress/build/screenCapture.npmPackageDependencyTree.svg)



# package.json

```json

{
    "author": {
        "name": "Nathan Rajlich",
        "email": "nathan@tootallnate.net",
        "url": "http://tootallnate.net"
    },
    "bugs": {
        "url": "https://github.com/TooTallNate/keypress/issues"
    },
    "dependencies": {},
    "description": "Make any Node ReadableStream emit \"keypress\" events",
    "devDependencies": {},
    "directories": {},
    "dist": {
        "shasum": "1e80454250018dbad4c3fe94497d6e67b6269c77",
        "tarball": "https://registry.npmjs.org/keypress/-/keypress-0.2.1.tgz"
    },
    "homepage": "https://github.com/TooTallNate/keypress#readme",
    "keywords": [
        "keypress",
        "readline",
        "core"
    ],
    "license": "MIT",
    "main": "index.js",
    "maintainers": [
        {
            "name": "tootallnate",
            "email": "nathan@tootallnate.net"
        }
    ],
    "name": "keypress",
    "optionalDependencies": {},
    "readme": "keypress\n========\n### Make any Node ReadableStream emit \"keypress\" events\n\n\nPrevious to Node 'v0.8.x', there was an undocumented '\"keypress\"' event that\n'process.stdin' would emit when it was a TTY. Some people discovered this hidden\ngem, and started using it in their own code.\n\nNow in Node 'v0.8.x', this '\"keypress\"' event does not get emitted by default,\nbut rather only when it is being used in conjuction with the 'readline' (or by\nextension, the 'repl') module.\n\nThis module is the exact logic from the node 'v0.8.x' releases ripped out into its\nown module.\n\n__Bonus:__ Now with mouse support!\n\nInstallation\n------------\n\nInstall with 'npm':\n\n''' bash\n$ npm install keypress\n'''\n\nOr add it to the '\"dependencies\"' section of your _package.json_ file.\n\n\nExample\n-------\n\n#### Listening for \"keypress\" events\n\n''' js\nvar keypress = require('keypress');\n\n// make 'process.stdin' begin emitting \"keypress\" events\nkeypress(process.stdin);\n\n// listen for the \"keypress\" event\nprocess.stdin.on('keypress', function (ch, key) {\n  console.log('got \"keypress\"', key);\n  if (key && key.ctrl && key.name == 'c') {\n    process.stdin.pause();\n  }\n});\n\nprocess.stdin.setRawMode(true);\nprocess.stdin.resume();\n'''\n\n#### Listening for \"mousepress\" events\n\n''' js\nvar keypress = require('keypress');\n\n// make 'process.stdin' begin emitting \"mousepress\" (and \"keypress\") events\nkeypress(process.stdin);\n\n// you must enable the mouse events before they will begin firing\nkeypress.enableMouse(process.stdout);\n\nprocess.stdin.on('mousepress', function (info) {\n  console.log('got \"mousepress\" event at %d x %d', info.x, info.y);\n});\n\nprocess.on('exit', function () {\n  // disable mouse on exit, so that the state\n  // is back to normal for the terminal\n  keypress.disableMouse(process.stdout);\n});\n'''\n\n\nLicense\n-------\n\n(The MIT License)\n\nCopyright (c) 2012 Nathan Rajlich &lt;nathan@tootallnate.net&gt;\n\nPermission is hereby granted, free of charge, to any person obtaining\na copy of this software and associated documentation files (the\n'Software'), to deal in the Software without restriction, including\nwithout limitation the rights to use, copy, modify, merge, publish,\ndistribute, sublicense, and/or sell copies of the Software, and to\npermit persons to whom the Software is furnished to do so, subject to\nthe following conditions:\n\nThe above copyright notice and this permission notice shall be\nincluded in all copies or substantial portions of the Software.\n\nTHE SOFTWARE IS PROVIDED 'AS IS', WITHOUT WARRANTY OF ANY KIND,\nEXPRESS OR IMPLIED, INCLUDING BUT NOT LIMITED TO THE WARRANTIES OF\nMERCHANTABILITY, FITNESS FOR A PARTICULAR PURPOSE AND NONINFRINGEMENT.\nIN NO EVENT SHALL THE AUTHORS OR COPYRIGHT HOLDERS BE LIABLE FOR ANY\nCLAIM, DAMAGES OR OTHER LIABILITY, WHETHER IN AN ACTION OF CONTRACT,\nTORT OR OTHERWISE, ARISING FROM, OUT OF OR IN CONNECTION WITH THE\nSOFTWARE OR THE USE OR OTHER DEALINGS IN THE SOFTWARE.\n",
    "readmeFilename": "README.md",
    "repository": {
        "type": "git",
        "url": "git://github.com/TooTallNate/keypress.git"
    },
    "scripts": {
        "test": "echo \"Error: no test specified\" && exit 1"
    },
    "version": "0.2.1"
}
```



# misc
- this document was created with [utility2](https://github.com/kaizhu256/node-utility2)
