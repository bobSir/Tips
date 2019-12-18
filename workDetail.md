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








