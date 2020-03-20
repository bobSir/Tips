## 小程序秒开 2019-11-28 10:21:45

1. 获取pagejson -> 解析
2. 单个请求限制时间3s

## 小程序整体优化 2019-12-02 09:50:28 @cly

### 页面打开速度优化

1. 分析耗时
2. 布局优化 viewStub 减少布局层次 过度绘制
3. 小程序打开优化 
4. 小程序资源包下载分析，优化

#### 打开小程序耗时分析
- 资源包流程 资源包大小1.5m
- 下载资源包耗时(4000ms) -> 写入磁盘(50ms) -> 解压(270ms) ->  入库(70ms) 
- 本地存在启动耗时 400ms

- 空宿主包5.8m  依赖fund-playground-whole后体积12.8m  增加7m
+--- com.eastmoney.android.usertrack:fund-usertrack:0.1.0 (126kb)

+--- com.amap.api:location:3.7.0 (335kb)

+--- com.lzy.widget:imagepicker:0.6.1 (120kb)

+--- com.github.bumptech.glide:glide:4.0.0 

+--- com.caverock:androidsvg-aar:1.3 (221kb)
w
+--- com.eastmoney.android.fundweex:fund-gcanvas:0.1.1-SNAPSHOT {java(73kb) armeabi(350kb+719kb) armeabi-v7a(350kb+703kb)}

+--- com.eastmoney.android.fundweex:lottie:2.6.2 (296kb)

+--- com.eastmoney.android.fundweex:fund-richtext:0.1.0.1-SNAPSHOT (197kb)
|    \--- org.greenrobot:eventbus:3.1.1

+--- com.eastmoney.android.fundweex:fund-playground-whole:0.3.0 (806kb)
|    +--- com.eastmoney.android.fundweex:fund-playground:0.6.33-SNAPSHOT (1.3m)
|    |    +--- com.eastmoney.android.fundweex:fundweex-libutil:0.0.4 (63kb)
|    |    +--- com.eastmoney.android.fundweex:lib-weex:0.28.0.7 {java(1.3m) armeabi(9.8m) armeabi-v7a(9.8m)}
|    |    |    +--- com.taobao.android:weex_inspector:0.10.0.5
|    |    |    +--- com.taobao.android:weexplugin-loader:1.3
|    |    |    \--- com.alibaba:fastjson:1.2.58
|    |    +--- com.eastmoney.android.fundweex.bindingx:weex_plugin:1.0.3.7 (97kb)
|    |    |    \--- com.eastmoney.android.fundweex.bindingx:core:1.0.9.2 (138kb)
|    |    +--- com.taobao.android:weexplugin-annotation:1.3
|    |    +--- com.squareup.okhttp3:okhttp:3.12.0 (*)
|    |    +--- com.google.code.gson:gson:2.8.5
|    |    +--- org.greenrobot:eventbus:3.1.1 (60kb)
|    |    +--- net.lingala.zip4j:zip4j:1.3.2 (140kb)
|    |    +--- x5 (385kb)
|    |    \--- com.google.zxing:core:3.3.0
|    +--- com.squareup.okhttp3:okhttp:3.12.0 (*)
|    +--- com.google.code.gson:gson:2.8.5
|    \--- org.greenrobot:eventbus:3.1.1


## 资讯 热更新&秒开 技术方案+实现

### 列表热更新 <-> itemView的样式

- 需要已知+计划+未来 item样式，根据itemView复杂度确定使用热更新，

### 业务对接

#### 列表逻辑

 1. 交互
 2. 本地记录
 3. 多少种布局类型

#### 资讯正文 类型 

 1. 图片
 2. 视频
 3. 短链
 4. 产品交互 上次阅读位置
 
#### 原生布局 webview

 - 正文title
 - 关键词
 - 正文底部点赞
 - 不感兴趣
 - 分享
 - 工具栏
 - 评论列表

### 热更新实现

### 技术实现方案

- 列表热更新方案 jsonView item布局动态更新
- 正文预加载H5模板

#### 列表

- 推荐列表 其他列表
- 获取正文内容
- 埋点
- jsonView
1. 确定布局样式 jsonView编写
2. 更新方案
3. 点击态 文本置灰api
4. 业务逻辑 置顶 上次看到这里
5. 交互UI
6. 快讯列表

- 推荐列表需求
1. http://172.16.89.168/redmine/issues/203202
2. http://172.16.89.168/redmine/issues/237424


#### 正文

- 埋点

1. H5模板
2. 模板动态更新
2. 正文内容先加载，其余页面信息懒加载
3. JS - 原生 交互
4. 原生工具栏

### 资讯秒开笔记

- FundNewsFlowNewsItemView.class 资讯详情跳转
- 资讯接口文档 https://appnewstest.1234567.com.cn/FundCMS.ApiDoc/swagger/ui/index#/

http://gubadoc.eastmoney.com/gubaapi/index.php?s=/4&page_id=221
1.2 赞帖子（投资组合，新闻，公告，研报，普通帖，自媒体文章，自媒体话题等）
1.4 取消赞帖子（投资组合，新闻，公告，研报，普通帖，自媒体文章，自媒体话题等）
1.6 赞回复（投资组合，新闻，公告，研报，普通帖）
1.8 取消赞回复（投资组合，新闻，公告，研报，普通帖）

1.1  http://gubadoc.eastmoney.com/gubaapi/index.php?s=/4&page_id=214
东财app 发帖接口
访问密码：1df06543210cf1

### TODO

#### 资讯详情正文
1. 打开不同类型文章
2. 样式&短链跳转

#### 中间内容
1. 关键词
2. 点赞&分享
3. 广告
4. 相关推荐

#### 评论列表&底部功能区

- 异常页面

#### 模板更新
#### js - NATIVE 交互
//预加载资讯详情
- preloadNewsData({  
	articleType:'',
	articleId:''
})

//显示回复键盘
- showReplyKeyboard({
	reply:{
		id:'',
		userName:''
	},
	success:(res) => {

	}
})

//分享
- showShare({
	articleType:'',
	articleId:''
})

//微信
- shareWeChat({
	type:'' //微信weChat、朋友圈wCFriends
	articleId:''
})

//通用短链
- commonLinkTo({
	url:''
})

//跳转个人主页
- navigateToUserHostHome({
	
})

//图片浏览
- previewImage({
	urls:
})


## 评论列表
### 资讯&财富号
- https://appnewstest.1234567.com.cn/FundCMS.ApiDoc/swagger/ui/index#!/AppService/AppService_GetNewsReplyList

### 帖子&回答
- http://10.228.130.163:7201/home/project?name=%E5%9F%BA%E9%87%91%E5%90%A7%E6%96%B0%E6%8E%A5%E5%8F%A3#Fund_MBNew_Api_FundMBNewController_UserPointConfigureNew_Fund_MBNew_Api_Model_Request_UserPointRequest625_
- ArticleReplys 
- 密码 dddwwwse2232ddZA22

- 数据结构不一样！

### 赞回复
- http://10.228.129.227:8181/swagger-ui.html#!/3103821306361643575925805203162550921475/likeArticleReplyUsingPOST

### 帖子 问答 评论
- http://10.228.130.163:7201/home/returnmodel?typename=Fund.MBNew.Api.FundMBNewController&actionname=Reply  返回参数
- FundBarCommentReplyActivity #378

#### 回复帖子
- url:https://fundmobapitest2.eastmoney.com/FundMCApi/FundMBNew/Reply
- params:appType=ttjj&t_type=0&userid=41fbf9a73b9d4de1bc4642f34ec4a45e&product=EFund&type=0&Version=6.2.5&ReqNo=1577359958096&keywordlist={}&deviceid=fab64d45af7318f3bedde4f054ace216||124844930637568&cccccccTokenErrorStop=true&huifuid=&text=[赞]&cToken=6fk86fd-fjn-qf81kcukk-8cnqrcrf8e&newsid=&tid=891191254&is_repost=false&uToken=8h-8kfq8dcd6k-dd--1jfqkqcafahan8&plat=Android&passportid=1010285287738720

#### 回复评论
- url:https://fundmobapitest2.eastmoney.com/FundMCApi/FundMBNew/Reply
- params:appType=ttjj&t_type=0&userid=41fbf9a73b9d4de1bc4642f34ec4a45e&product=EFund&type=0&Version=6.2.5&ReqNo=1577360052973&keywordlist={}&deviceid=fab64d45af7318f3bedde4f054ace216||124844930637568&cccccccTokenErrorStop=true&huifuid=8840285945&text=[赞]&cToken=6fk86fd-fjn-qf81kcukk-8cnqrcrf8e&newsid=&tid=894389199&is_repost=false&uToken=8h-8kfq8dcd6k-dd--1jfqkqcafahan8&plat=Android&passportid=1010285287738720

### 资讯 财富号 评论
- FundCommentReplyActivity 395

#### 回复文章
- https://appnews.1234567.com.cn/api/AppService/ReplyArticle
- params:t_type=1&UserId=41fbf9a73b9d4de1bc4642f34ec4a45e&passportId=1010285287738720&gToken=ceaf-17bc7941d8177946da41795a240de157&type=0&Plat=Android&OSVersion=7.1.1&text=[赞]&isRepost=false&MarketChannel=AndroidMarket&DeviceId=fab64d45af7318f3bedde4f054ace216||124844930637568&artCode=201912261337426837&huifuId=0&cToken=6fk86fd-fjn-qf81kcukk-8cnqrcrf8e&pitype=0&appVersion=6.2.5&MobileKey=fab64d45af7318f3bedde4f054ace216||124844930637568&uToken=8h-8kfq8dcd6k-dd--1jfqkqcafahan8&key=a8eb1746-1375-8def-b5e8-fe369ee73d68

#### 回复评论
- url:https://appnews.1234567.com.cn/api/AppService/ReplyArticle
- params:t_type=1&UserId=41fbf9a73b9d4de1bc4642f34ec4a45e&passportId=1010285287738720&gToken=ceaf-17bc7941d8177946da41795a240de157&type=0&Plat=Android&OSVersion=7.1.1&text=[赞]&isRepost=false&MarketChannel=AndroidMarket&DeviceId=fab64d45af7318f3bedde4f054ace216||124844930637568&artCode=201912261337426837&huifuId=8840226409&cToken=6fk86fd-fjn-qf81kcukk-8cnqrcrf8e&pitype=0&appVersion=6.2.5&MobileKey=fab64d45af7318f3bedde4f054ace216||124844930637568&uToken=8h-8kfq8dcd6k-dd--1jfqkqcafahan8&key=a8eb1746-1375-8def-b5e8-fe369ee73d68

## 中间内容
- FundCFHRecentlyNewsView 80 最近更新
- FundRelateNewsView 103 相关资讯

- 广告 资讯 & 财富号 包在正文中  admodel  帖子&问答 FundBarFunctions #262
- 点赞文章 FundBarFunctions 262 4合一
- 不感兴趣 FundBarFunctions 494 回答没有
- 打赏 帖子 跳转
- 收藏 FundBarFunctions 413 取消


# TODO

## 资讯详情

### 接口替换 
- 列表

- 正文 关键词匹配

### 正文
- 上次阅读
- 阅读全文
- 视频 (资讯视频 财富号视频)
- 查看原文链接
- 图片浏览
- UI还原

### 中间内容
- UI
- 数据绑定
- 打赏
- 分享
- 广告
- 相关推荐 or 最近更新
- 业务逻辑梳理
- 评论操作区
- UI还原

### 评论区
- UI
- 数据绑定 数据交互
- 评论原生交互
- 评论表情
- 评论图片
- UI还原
- 分享

### 细节

- 交互细节


## 资讯列表

### 接口对接
- 自选基金 资讯 + 公告
/cms/getlist
- 个股资讯
/api/fund/ann
- 资讯页tab
/api/v1/fund/


- 七巧板




## 业务整理

### 页面整理

### 接口整理








































