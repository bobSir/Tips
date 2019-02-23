## 2019/02/11
1. 连接远程服务器 sudo su -，ssh -p 22 root@207.148.125.203, 退出logout
2. [I/O优化](https://time.geekbang.org/column/article/74988) 页缓存 地址映射

## 2019/02/12
### okHttp socket通信
- WebSocket  OkHttpClient.newWebSocket(request,WebSocketListener)[anyChat WebSocketManager.java]
### 工作总结
### 面试题归纳，解答

## 2019/02/13
1. Http headers、拦截器、取消网络请求、tag,okHttpClient.dispatcher().queueCalls()、okHttpClient.dispatcher().runningCalls()、call.cancel()

## 2019/02/14
### 线程
- Thread.join():可以将2个交替执行的线程合并为顺序执行的线程。比如在线程B中调用线程A的join()方法，直到线程A执行完，才会继续执行线程B。
- Callable:类似于Runnable的接口，1、自定义一个类 MyCallable 实现 Callable 接口，并重写call()方法
2、将要执行的代码写在call()方法中
3、创建线程池对象，调用submit()方法执行MyCallable任务，并返回Future对象
4、调用Future对象的get()方法获取call()方法执行完后的值

### 多线程
- 优点：提高cpu使用率，提高程序工作效率。
- 缺点：大量线程会影响性能，cpu需要线程切换，更多内存空间，多线程操作可能会出现线程安全或者死锁等问题。
- 线程安全：多个线程操作共享数据，多线程并发。操作共享数据代码块用synchronized进行同步、Lock.lock()同步锁，完成后unlock()解锁。
- ReentrantLock 等待可中断，公平锁，锁绑定多个条件

#### 线程池[详解](https://mp.weixin.qq.com/s?__biz=MzIxNzU1Nzk3OQ==&mid=2247486898&idx=1&sn=ae909df0b82ce8d1780bde223f388620&chksm=97f6b306a0813a107a15e0d999358073a66d7184b1e792536c27b213516e0daa1f5a6fbfd2e1&scene=38#wechat_redirect)
1. ThreadPoolExecutor: Executor的实现类，Android中的线程池都是直接或间接通过配置ThreadPoolExecutor来实现不同特性的线程池。
2. Executors 创建常用线程池的静态方法。
FixedThreadPool: 定长线程池
SingleThreadExecutor: 单线程化线程池
ScheduledThreadPool: 定时线程池
CachedThreadPool: 缓存线程池

#### 线程组[详解](https://mp.weixin.qq.com/s?__biz=MzA5MzI3NjE2MA==&mid=2650243240&idx=1&sn=e932f64adfbdfa8e7f6a7455c78df1a6&chksm=886371c7bf14f8d17a280c8095e6f21a41a3a8dd7177c5909e2d9d965cae82da9b0b210614ed&scene=38#wechat_redirect)
- 实现对多个线程的管理，线程池注重是利用多个线程执行大量的任务。

#### 实践 eastmoney_threadpool
- ScheduledExecutorService
- 根据cpu创建最大线程数
- 支持线程组，组内优先级
- 自定义实现AsyncTask功能


## 2019/02/15
1. Transition框架,[动画](https://mp.weixin.qq.com/s?__biz=MzIwMzYwMTk1NA==&mid=2247490612&idx=1&sn=c14add48a4fc7237195d74967a09c835&chksm=96cdbd79a1ba346f7f7a932400e7368f586394437742bd23d3da98971b0580eb17c10a09a2ce&mpshare=1&scene=1&srcid=0215PDH6JzsIqU0W3LFPNRod&key=52682f658a905933dfbfe2c2d21fc45fb58875edf2abca897ebd1e347d4ad9461de1e7c7590b0a40fd7862b12f892607506a41cc4365d58377314d09927261d2d4ff65d22e5261b975c830e72ba0b902&ascene=0&uin=MTY3NzY1MzQ4MQ%3D%3D&devicetype=iMac+MacBookPro12%2C1+OSX+OSX+10.10.5+build(14F2511)&version=11020012&lang=zh_CN&pass_ticket=bSi7d9YrcExMFLdu%2Fi6BC3TX657Y4y2XFwshJheHoPhzrkF0NlvDoM6RLur%2BUS3X)

## 2019/02/19
### okHttp缓存源码分析
- CacheInterceptor、DiskLruCache、请求体转成MD5作为key、源码实现兼容服务端heads cache-control决定是否缓存、自定义网络缓存实现模仿CacheInterceptor实现由客户端控制。

### Handler
- 跨线程通信、Message、MessageQueue、Handler、Looper.
- MainThreadDelivery 回调至主线程封装类
- 内存泄漏、handler.removeCallbacksAndMessages(null)

## 2019/02/21
### Android Studio NDK坑
- 在fundWeex Android项目中限制使用ndk16，安装CMAKE，安装ninja，编译没有报相关ninja，CMAKElog中没有说明需要安装ninja，安装完ninja正常编译，brew install ninja。
- anyChat中NDK版本为ndk16，安装最新Android sdk对应NDK版本为19，手动下载NDK16，配置NDK16路径。



















