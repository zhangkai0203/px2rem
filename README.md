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

#### postcss-pxtorem移动端适配
```
npm install postcss-pxtorem -D
```

#### postcss.config.js 新建package.json同一个目录下，文件内容如下
```
module.exports = {
  plugins: {
    'autoprefixer': {
      browsers: ['Android >= 4.0', 'iOS >= 7']
    },
    'postcss-pxtorem': {
      rootValue: 32,//结果为：设计稿元素尺寸/16，比如元素宽320px,最终页面会换算成 20rem
      propList: ['*']
    }
  }
}
```
#### 在根目录src中新建util目录下新建rem.js等比适配文件
```
const baseSize = 32
// 设置 rem 函数
function setRem () {
// 当前页面宽度相对于 375 宽的缩放比例，可根据自己需要修改。  vantUI使用的人375px页面宽，这里使用375px
const scale = document.documentElement.clientWidth / 375
// 设置页面根节点字体大小
document.documentElement.style.fontSize = (baseSize * Math.min(scale, 2)) + 'px'
}
// 初始化
setRem()
// 改变窗口大小时重新设置 rem
window.onresize = function () {
    setRem()
}
```
#### 在 main.js中引入 rem.js 文件，然后启动项目
```
import './utils/rem.js';
```
