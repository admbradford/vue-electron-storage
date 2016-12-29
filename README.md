# vue-electron-storage
> A vue plugin that wraps [electron-storage](https://github.com/Cocycles/electron-storage) APIs to the Vue object.

[![js-standard-style](https://cdn.rawgit.com/feross/standard/master/badge.svg)](https://github.com/feross/standard)

## Installing
Install using NPM
```
npm install vue-electron-storage --save
```

Include using webpack or browserify

**main.js**
```js
import Vue from 'vue'
import VueElectronStorage from 'vue-electron-storage'

Vue.use(VueElectronStorage)
```

## Using the plugin
This plugin will attach electron APIs to the Vue object itself, so accessing all APIs is dead simple. All official documentation from electron can be used and accessed from `this.$storage`.

So instead of...
```js
const storage = require('electron-storage')

export default {
  methods: {
    checkFileExists (path) {
      storage.isPathExists(path, (itDoes) => {
        if (itDoes) {
          console.log('pathDoesExists !')
        }
        return itDoes
      });
    }
  }
}
```

Now you can...

```js
export default {
  methods: {
    checkFileExists (path) {
      this.$storage.isPathExists(path, (itDoes) => {
        if (itDoes) {
          console.log('pathDoesExists !')
        }
        return itDoes
      });
    }
  }
}
```

Now you might be thinking, "Is it really that annoying to simply require electron to access it?" Probably not, but it can get cumbersome to have to include it in every component file that needs it. In the end, attaching electron storage directly to Vue just makes sense.
