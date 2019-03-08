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

## NDK







