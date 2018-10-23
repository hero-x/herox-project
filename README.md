>整理一下从开年来到现在自己做的上线的项目。开此贴的目的就是为了记录下到目前为止自己所做的项目并且总结。（ps.有的项目已经做了太久，具体的详情也记不太清了，就简单的记录下。）

### 平安30周年'爱你一下'(已下线)

时间:2018.4~2018-6

项目地址:[爱你一下抽奖](http://h5.xhangjia.com/2018/10/pingan_lottery/#/)

项目介绍:这是一个webview的项目，我主要负责抽奖。项目用到了帧动画，然后由于是内置到APP内的，兼容andriod5.0以及ios8.0。活动性项目,目前已下线。

技术栈:Vue全家桶

ps:由于项目下线，所以抽奖为模拟数据。

### 青年驿站(小程序,待上线)


时间:2018.6~2018-7

项目介绍:大学生来深圳可以在青年驿站免费入住7天。目前该项目处于资料补充阶段，不久将会上线。

主要功能:深圳政策新闻、驿站浏览申请、工作招聘信息、活动报名发起或者参加、个人中心、会员管理等等。一共有七十多个页面，属于比较大的小程序。

技术栈:Wepy(类vue语法的框架)

遇到的困难:
1. 小程序图片上传到OSS
2. 地图功能用户取消授权重新唤起授权处理(微信小程序自带的坑)

问题的解决过程参考：[小程序踩坑指北](https://hero-x.cn/2018/06/22/weapp/)

截图:

![](https://ws4.sinaimg.cn/large/006tNbRwgy1fw8wppxazsj30ad0iigmv.jpg)

![](https://ws1.sinaimg.cn/large/006tNbRwgy1fw8wq2i8x3j30a80ih75c.jpg)
![](https://ws4.sinaimg.cn/large/006tNbRwgy1fw8wq8huynj30ab0ihjro.jpg)
![](https://ws3.sinaimg.cn/large/006tNbRwgy1fw8wqd8zyyj30ab0ig74w.jpg)
![](https://ws1.sinaimg.cn/large/006tNbRwgy1fw8wqhiov5j30a90ii0sw.jpg)


### 平安校招PC版(已上线)

时间:2018.7~2018.9

项目地址:[校招线上地址](http://campus.pingan.com/)

项目介绍:平安校招全新改版。为19年校招投入使用，目前已上线。项目很大，我主要负责简历页、简历预览页、个人中心页、职位列表、职位详情、职位投递等模块。兼容各大浏览器,ie的话兼容到ie9。

主要功能:我负责的模块中，职位列表页可以浏览职位，搜索职位，投递职位；个人中心页可以看到自己的投递信息，下载简历PDF等等；简历页可以编辑简历以及投递自己的简历等等...

技术栈:Nuxt、vue全家桶、elementui...

遇到的困难:

1. 头像上传。简历页有一个头像上传到oss的功能，由于头像是截取后转化为Blob格式上传，在ie下存在Blob兼容性问题，故先判断是否为IE，是IE的话拿到Blob格式的文件 转化为formData,再进行上传，完美解决。
2. 职位搜索功能。职位搜索涉及到的关键词比较多，加上底部还有分页功能，故在这里使用Vuex来进行搜索关键词的保存。具体功能见[校招职位列表页](http://campus.pingan.com/post)

截图:

![](https://ws2.sinaimg.cn/large/006tNbRwgy1fw8xer4jz9j31kw0u9nnf.jpg)
![](https://ws4.sinaimg.cn/large/006tNbRwgy1fw8xf4fvvij31kw0ucq56.jpg)
![](https://ws4.sinaimg.cn/large/006tNbRwgy1fw8xfdsyboj31kw0ubmyy.jpg)
![](https://ws3.sinaimg.cn/large/006tNbRwgy1fw8xfnt6b8j31kw0ubdik.jpg)


### 平安校招MOBILE版(已上线)

时间:2018.9~2018.10

项目地址：[校招线上地址](https://m-campus.pingan.com/#/)

项目介绍:同PC端，不过这个微官网是全部由我一个人完成的(成就感满满!)。移动端脚手架的配置参考我这篇文章-->[Vue移动端项目搭建](https://hero-x.cn/2018/08/24/vue-mobile-start/)

主要功能:同PC端。多的功能就是支持微信分享以及扫码进入。

技术栈:vue全家桶、vantui...

遇到的困难:

1. 还是头像的上传。uc跟扣扣浏览器兼职就是移动端的IE6!!!后面实在是没办法了，才让后台java小哥哥做了个接口，我这边只传blob给后台，后台来负责上传到oss。
2. 在打包后，发现部分机型自带的浏览器(黑莓浏览器、华为浏览器等)在职位意向页点击下一步无响应。通过vconsole最后定位到是`photoclip`插件的es6语法未被转义到es5，导致不兼容es6的浏览器报错。修改`webpack.base.conf.js`

```javascript
 module: {
        rules: [
            ...,
            {
                test: /\.js$/,
                loader: 'babel-loader',
                options: {
                    presets: ['es2015']
                },
                include: [resolve('src'), resolve('test'),resolve('/node_modules/photoclip')]
            },
            ...,
        ]
    }
```

截图:

![](https://ws3.sinaimg.cn/large/006tNbRwgy1fw8xvkf6q1j30kc10sn1f.jpg)
![](https://ws1.sinaimg.cn/large/006tNbRwgy1fw8xvys886j30km10qjsq.jpg)
![](https://ws4.sinaimg.cn/large/006tNbRwgy1fw8xw3j6qpj30kk10yweo.jpg)


### 百度easyDl(pc+moblie)(已上线)

时间:2018.10

项目地址:

[pc入口](http://ai.baidu.com/easydl/empower/pc/index.html)

[MOBILE入口](http://ai.baidu.com/easydl/empower/mobile/index.html#/)

项目介绍:百度大脑行业应用创新挑战赛。有PC端和MOBILE端,都有一个首页和一个表单页。目前已上线使用

技术栈:由于页面较少，开发周期较短，所以PC端使用了Jquery进行开发，在表单页涉及到表单的校验以及提交，所以引入了elementui;MOBILE端由于不涉及SEO，则使用的是Vue脚手架来进行快速开发。移动端脚手架的配置参考我这篇文章-->[Vue移动端项目搭建](https://hero-x.cn/2018/08/24/vue-mobile-start/)

截图:

PC端: 

![](https://ws3.sinaimg.cn/large/006tNbRwgy1fw8wgt0cqsj31h60q0qlq.jpg)

![](https://ws4.sinaimg.cn/large/006tNbRwgy1fw8wh8sw3oj31h60q0qlq.jpg)

MOBILE端:

![](https://ws4.sinaimg.cn/large/006tNbRwgy1fw8wihgq61j30ku11i7ha.jpg)

![](https://ws1.sinaimg.cn/large/006tNbRwgy1fw8wl67a18j30kw11en0q.jpg)

总结:以上就是我在2018.10之前所做的所有项目，其实还有个活动的h5，但是由于过了太久就没放出来。所以一共是4个上线项目加一个待上线的小程序项目。入职这么久以来，收获多多。