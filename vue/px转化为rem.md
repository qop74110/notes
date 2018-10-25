# px转化为rem，适配移动端

### 项目中引入lib-flexible
> 1.下载lib-flexible

```
npm i lib-flexible --save
```

> 2.引入lib-flexible
在main.js中引入lib-flexible
```
import 'lib-flexible'
```

### 使用px2rem-loader自动将css中的px转换成rem

> 1.安装px2rem-loader

```
npm install px2rem-loader --save-dev
```
> 2.配置px2rem-loader

1.  打开build/utils.js文件，找到exports.cssLoaders方法，在里面添加如下代码

```javascript
const px2remLoader = {
    loader: 'px2rem-loader',
    options: {
      remUint: 75
    }
  }
```
2. 打开build/utils.js文件，找到generateLoaders方法 

```javascript
function generateLoaders(loader, loaderOptions) {
    var loaders = [cssLoader, px2remLoader];                //  1.添加px2remLoader 插件
    if (loader) {
      loaders.push({
        loader: loader + '-loader',
        options: Object.assign({}, loaderOptions, {
          sourceMap: options.sourceMap
        })
      })
    }   
 }
```

3. build/utils.js文件 添加 generateSassResourceLoader方法
```javascript
    function generateSassResourceLoader () {                
       const loaders = [
          cssLoader,
          px2remLoader,
          'less-loader'
       ]
       if (options.extract) {
          return ExtractTextPlugin.extract({
             use: loaders,
             fallback: 'vue-style-loader'
          })
       } else {
           return ['vue-style-loader'].concat(loaders)
       }
    }
```

4. 修改 build/utils.js文件 return
```javascript
    return {
        css: generateLoaders(),
        postcss: generateLoaders(),
        less: generateSassResourceLoader()                //  修改less的值
    } 
```

5. 修改/node_modules/px2rem-loader/lib/px2rem-loader.js
```javascript
var loaderUtils = require('loader-utils')
var Px2rem = require('px2rem')

module.exports = function (source) {
  var options = loaderUtils.getOptions(this)
  if (/node_modules/.test(this.resourcePath)) return source
  var px2remIns = new Px2rem(options)
  return px2remIns.generateRem(source)
}
```

### 重启，一切ok~
```
npm run dev
```