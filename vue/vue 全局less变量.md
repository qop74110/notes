# vue 全局less sess变量

1.安装

```
npm install sass-resources-loader
```

2.配置
```
module: {
  rules: [
    {
      test: /\.scss$/,
      use: [
        'style-loader',
        'css-loader',
        'postcss-loader',
        'sass-loader',
        {
          loader: 'sass-resources-loader',
          options: {
            // Provide path to the file with resources
            resources: './path/to/resources.scss',
 
            // Or array of paths
            resources: ['./path/to/vars.scss', './path/to/mixins.scss']
          },
        },
      ],
    },
  ],
},
```

[sass-resources-loader文档](https://www.npmjs.com/package/sass-resources-loader)