# wap app 适配方式

#### amfe-flexible 控制html中font-sieze大小
```
cnpm install amfe-flexible -S
import 'amfe-flexible';
```

#### postcss-px2rem 把px转成rem
```
cnpm install postcss-px2rem -D
```

#### 创建vue.config.js
```
module.exports = {
	lintOnSave: true,
	css: {
		loaderOptions: {
		  css: {},
		  postcss: {
			plugins: [
			  require('postcss-px2rem')({
				remUnit: 37.5 //设计图 37.5 = 375/10
			  })
			]
		  }
		}
	},
}
```
#### 重新启动服务即可
```
提示：如果不想装换 可以使用大写的PX或Px
```
