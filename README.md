# cvms-with-vue
## 如何在cvms项目中结合webpack与vue开发  
- 在app目录下新建build文件夹，所有vue单文件模板都放在这个文件夹中，
build文件夹的结构与vuecli生成src目录结构一样。webpack打包生成的app.min.js放入public/static/js/中。
## webpack的配置  
除了一些loader的配置外，还要加上以下选项
```json
 resolve: {
        alias: {
            'vue': 'vue/dist/vue.js'
        }
   }
```  
### 提取vue单文件中的style到css文件  
```json
 {
            test: /\.vue$/,
            loader: 'vue-loader',
            options: {
            loaders: {
                css: ExtractTextPlugin.extract({
                    use: 'css-loader',
                    fallback: 'vue-style-loader'
                    }),
                },
            }

}
plugins: [
    new ExtractTextPlugin('../css/appstyle.css')
]
```  
另外需要安装 vue-template-compiler 
### babel配置  
```json
{
    "presets": [
        "es2015",
        "stage-2"
    ]
}
```  
需要安装依赖  
```
    "babel-core": "^6.24.0",
    "babel-loader": "^6.4.0",
    "babel-preset-es2015": "^6.24.1",
    "babel-preset-stage-2": "^6.24.1",
```


