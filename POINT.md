# POINT

## 内存

- 设备分级、device-year-class

- Bitmap优化、远超View宽高，超屏幕大小。加载重复图片

- 内存泄露 LeakCanary

- 内存泄露、减少内存申请、及时回收、减少常驻内存、精简布局、图片。

- Android Bitmap内存分配变化，bitmap对象、像素数据。
- Java堆中、Native内存，Android Low memory killer。
- Fresco在Dalvik会把图片放到Native内存中。

### Matrix：开源APM

### Dalvik ART 虚拟机

## handler

- handler,looper,Message,MessageQueue
- 子线程中创建Handler,Looper.prepare()->new Handler()->Looper.loop()
- PostDelay(),postDelay的Message并不是先等待一定时间在放到MessageQueue中，而是直接放入并阻塞当前线程，然后将其delay的时间和对头的进行比较，按照触发时间进行排序。

## service

- startService(intent) onCreate->onStartCommand->onDestroy,stopService(intent)。Service单独任务，与Activity没有通信。

- bindService(intent,ServiceConnection,flag) onCreate->onBind->onDestroy，unBindService(ServiceConnection)。与Activity建立通信。销毁Service(onDestroy) 解绑(如果有bindService)，stop(如果有startService)。

- Service是运行在主线程的，在Service中执行耗时操作会ANR，理解为后台任务，生命周期与进程相关。可以在Service中启子线程完成耗时操作。所有的Activity都能和Service进行关联获取的是原有Service中Binder实例。

- 前台Service，在onCreate中实现Notification，使其显示于状态栏。

- [郭霖Service解析](https://blog.csdn.net/guolin_blog/article/details/11952435)

## [事件分发](https://www.jianshu.com/p/e99b5e8bd67b)
![图解](https://upload-images.jianshu.io/upload_images/966283-b9cb65aceea9219b.png)

- Activity->viewGroup->view
- dispatchTouchEvent()->onInterceptTouchEvent()->onTouchEvent()
- onTouch()->onClick()
- dispatchTouchEvent() activity->viewGroup->view, onTouchEvent() view->viewGroup->activity

## Socket[玉刚说](https://mp.weixin.qq.com/s?__biz=MzIwMTAzMTMxMg==&mid=2649492841&idx=1&sn=751872addc47d2464b8935be17d715d6&chksm=8eec8696b99b0f80b2ebb8e4c346adf177ad206401d83c17aca4047d883b0cc7c0788619df9d&scene=38#wechat_redirect)
- IP协议，提供了两个IP之间的通信
- TCP: 建立在IP的基础上，完成了主机与主机之间进程的通信。建立通信之前需要三次握手，
- UDP: 不需要经过握手，就可以直接发送数据
- Socket是TCP层的封装，通过socket，可以进行TCP通信。
- socket共有两个接口，用于监听客户连接的ServerSocket和用户通信的Socket

## HTTP & HTTPS
- http是超文本传输协议，信息是明文传输，https则是具有安全性的ssl加密传输协议。
- http和https使用的是完全不同的连接方式，用的端口也不一样，前者是80，后者是443。
- http的连接很简单，是无状态的；HTTPS协议是由SSL+HTTP协议构建的可进行加密传输、身份认证的网络协议，比http协议安全。


## [面试题目合集](https://www.jianshu.com/p/20754b1adb4d)

## RxJava

## NDK

## 团队影响力

## 业务推动力

## 沟通能力








