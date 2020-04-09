## 2019/02/11
1. 连接远程服务器 sudo su -，ssh -p 22 root@207.148.125.203, 退出logout
2. [I/O优化](https://time.geekbang.org/column/article/74988) 页缓存 地址映射

## 2019/02/12
### okHttp webSocket通信
- WebSocket  OkHttpClient.newWebSocket(request,WebSocketListener)[anyChat WebSocketManager.java]

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

## 2019/02/25
- VasSonic源码解析
- 预加载
- 缓存策略

## 2019/02/26
- [Apk反编译](https://mp.weixin.qq.com/s/nn-nwXnRI9JYSmknH1pzYg)

### webView加载优化
- webView池子
- webView预加载

## 2019/03/01

### 图表实现：webView加载H5，JS数据通信。eChat，highChart。

## 2019/03/08
- 构造函数 创建对象时执行
- 静态代码块 jvm加载类时执行，仅执行一次
- 构造代码块 创建对象时执行，在构造方法之前

## 2019/03/13
- Material Design 
- Ripple效果：android:background="?android:attr/selectableItemBackground" //波纹有边界 selectableItemBackgroundBorderless //波纹超出边界  可以自定义Ripple标签。
- Circular Reveal: ViewAnimationUtils.createCircularReveal(view,centerX,centerY,startRadius,endRadius)
- View state changes Animation: 视图改变时的动画效果，StateListAnimator。AnimationInflater.loadStateListAnimator() View.setStateListAnimator()分配动画到视图上。

## 2019/03/18
- IntentService vs Service
- onHandleIntent工作线程处理耗时任务，单线程流程处理任务。执行完任务自动停止。

## 2019/04/19
- <item name="android:windowBackground">@null</item>坑坑坑，style设置这个属性后activit不会回调到onStop，对Android系统来说这个activity是可见的只是不可交互、
- activity透明不要用这个属性，将windowBackGround设置为透明，overridePendingTransition（animEnter,animExit）, animExit也设置一个默认动画避免黑屏、

## 查看签名
keytool -list -v -keystore /Users/bob/AndroidWorkSpace/papa/mask.jks

## 2019/09/13
- 查看activity启动时间 在logcat中No Filters检索Displayed

## 2019/09/23
- activity finish()->onDestroy() 触发fragment onDestroy()时机不确定，不同手机fragment回调onDestroy()有不同程度的延迟，如果在fragment的onDestroy有业务逻辑处理的话，需要主动触发。

## 2019/09/24
- GlideException: Failed to load resource 检查加载图片地址是否前后有空格，或者引号，可以把url用GlideUrl(url)包起来检测查看异常信息。

## 2019/09/25
- WXSDKEngine weexSdk注册组件管理类

## 2019/09/29
- DialogFragment背景设置 颜色 高斯模糊...只是对弹窗设置和页面无关。
- 可以在子线程中操作UI 一个View在子线程中创建，在子线程中就可以操作该控件的UI，线程调度到主线程再添加到在主线程中创建的视图上即可完成展示，这样完成的视图如果需要再操作UI，要回到创建它的线程中操作才行。

## webSocket实现客户端热加载实践



## 2019/11/1 **Activity & Fragment传值区别**
- Activity & Fragment 通过Bundle传值区别：Activity底层通过Binder实现传值，Activity之间传值 sdk考虑到有可能跨进程，所以如果传值对象非基本数据类型都要主动实现序列化，来完成传值。Fragment之间传值，不为存在跨进程的场景，所以不用具体实现序列化的函数，也能正常完成传值。那么这里就会引发一个问题，传值如果只是值传递的话，就会在另一个Fragment中改变数据源的情况出现。所以在fragment中通过bundle传值，值要深拷贝。或者考虑其他传值方式。Java是传值引用，可以final修饰防止修改，Clone。

## 2019/11/5 修改aar重新打包 tar命令 压缩.tgz
- https://www.jianshu.com/p/f0a267551493
- $ jar cvf newAAR.aar -C tempFolder/ .
- tar czvf FileName.tgz path

## 2019/11/11 
- fragment为什么需要一个public的空构造器 android.support.v4.app.Fragment$InstantiationException: 异常原因是因为使用的fragment没有public的空构造器。源码通过Java反射机制实例化fragment。当应用被系统杀掉后回到前台，如果这个时候有UI呈现在Fragment中，那么因为restore造成fragment需要通过反射实例对象，从而将之前save的状态还原，这个反射就是fragment需要public的空构造器所在。
- transformClassesWithMultidexlistForDebug: 这个编译异常多半是因为程序中存在重复的包，可以通过./gradlew assembleDebug --stacktrace 输出详细log，定位重复包。

## 2019/11/12 SharedPreferences思考
- 文件xml 内存中map 同步锁实现线程安全 commit发生在UI线程 - 存储过大key value容易卡顿 aar apply发生在工作线程 放在线程池的任务队列中 表面不会阻塞UI线程 但在activity的onStop中源码handleStopActivity()中QueuedWork.waitToFinish()；如果apply的任务多，也会引起aar。
- 每次edit都会创建一个EditorImpl对象，修改或者添加都会将数据添加到mModifiled中，在commit或apply时比较mMap和mModifiled数据修正mMap再写入文件中。get是直接从map中读取如果存储大型的key或value他们会一直在内存中得不到释放。

## ABI so库
- 如果在gradle中指定输出多个abi，那么如果该工程还依赖其他so库，这个so要提供所有ABI的so库。
- 门面模式 接口隔离

## 混淆配置
- minifyEnabled true 开始混淆 把proguard配置打包进aar
```java
 defaultConfig {
        consumerProguardFiles 'proguard-rules.pro'
    }
```

## 2019/11/27 启动优化
- application不要做耗时操作，如必须可以等待必要操作完成再初始化，不要造成阻塞，开线程依然会占用系统资源(主要是CPU)，阻塞renderThread。
- 在实际测试中发现不同的手机厂商对application中的初始化，到程序主入口页面展示(manifest action.main)，中间的时间限制并不相同，这样在app启动速度对比中也会存在偏差。同等优化下小米的启动速度大于华为。

## 2019-12-02 13:44:45 buffer.toString()
- buffer.toString()源码实现，为了性能会截取字符串长度。readUtf8()输出所有。
- weex Post请求 body源码实现wson解析，map存储，最终是无序的。
- viewPager必须设置一个id，即使不使用。IllegalStateException: ViewPager with adapter com.fund.weex.lib.view.fragment.TopTabFragmentPagerAdapter@acf2ba8 requires a view id

## 2019-12-03 17:33:06 json解析异常
- 先检查数据格式类型

## 2019-12-04 13:27:24 
- logcat查看Activity启动时间 no Fliters 过滤关键词 ActivityManager 可以查看uid 启动耗时。
- artifactory java -jar artifactory-injector-1.1.jar -> 2 -> 设置home(artifactory解压目录) -> 生成license -> 执行artifactory.sh(windows artifactory.bat start) 

## 2020-2-3 锁 JDK层理解
- synchronized 排斥锁 对象锁 类锁、 静态方法，对象的锁相当于类锁，jvm中只存在一个。
- synchronized 隐式锁 1、没有中断 2、阻塞式获取锁
- 线程协作 Object.wait()释放锁  notify/notifyAll
- TheadLocal  threadLocal.set threadLocal.get  线程隔离 避免数据共享 每个线程数据副本
- Lock 显式锁 使用范式 finally中unlock()释放锁 可重入。
- 锁的公平与非公平 非公平锁 减少上下文切换时间，线程挂起 运行 操作系统会进行上下文切换。
- 读写锁 允许同时读写操作 不排斥，ReadWriteLock
- 悲观锁 乐观锁 读 写(compare and swap)
- Lock Condition实现等待通知 await singal
- 线程池 (线程数 最大线程数 存活时间 blockQueue rejected Ecutonhandle)
- 合理配置线程数 CPU密集型 机器最大线程数 Runtime.getRunTime.avialprocress IO密集型 
- AsyncTask 默认创建2个线程池 SerialExecutor()保征任务串行执行   ThreadPoolExecutor()执行异步任务  InternalHandler 消息通知主线程
- volatile 易变的 JDK提供的最轻量级的数据同步机制  保征可见性 不能保征原子性
- JVM 主内存 工作内存 每个线程都会有一个工作内存 工作内存数据操作后悔同步到主内存 线程读取操作数据只会在工作内存中读取。
- synchronized 本质上是锁对象 锁的是主内存中的对象。 volatile只是在读取的时候工作内存拉下主内存中的数据。只有一个线程写 其他线程读 volatile没有问题。

## RxJava 2020-02-10 21:54:09
- 观察者模式 响应模式
- 操作符
- 线程调度
- 背压 Flowable 4种策略

### 实际应用
- 网络请求 嵌套请求 轮询 出错重连
- 防双击
- 多级缓存获取数据
- 合并数据源

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
- PostDelay(),postDelay的Message并不是先等待一定时间在放到MessageQueue中，而是直接放入并阻塞当前线程，然后将其delay的时间和对头的进行比较，按照触发时间进行排序。其余事件可以唤醒线程。

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

## 快速滑动不加载图片
- onScrollListener - onScrollStateChanged{} RecyclerView.Scroll_STATE_IDLE & DRAGGING resume(), SETTLINE pause().
- Fresco.getImagePipeLine().resume()、Glide.with(context).resumeRequests().

## Bitmap加载优化
- BitmapFactory.decode**() BitmapFactory.options inJustDecodeBounds/inSmapleSize. 获取图片实际宽高，根据实际加载需要宽高压缩。解码器会对非2的幂的数
进行向下处理获取接近2的幂的数。
- Bitmap对象、像素数据。Android3.0之前Bitmap对象放在Java堆中，像素数据放在Native内存中，需要手动调用recycle。3.0~7.0Bitmap对象和像素数据都放在Java堆中，造成大量GC，系统内存没有利用起来。8.0 利用NativeAllocationRegistry辅助回收Native内存。
- Fresco在Dalvik中把图片放在Native内存中。调用libandroid_runtime.so中Bitmap构造函数，创建Java Bitmap，将Java bitmap内容绘制到Native Bitmap中，再回收Java Bitmap。频繁创建Java Bitmap容易引起内存抖动。

### Bitmap内存检测
- Bitmap创建统一接口，在接口层将所有被创建出来的Bitmap加入到一个WeakHashmap中，记录创建时间、堆栈信息，在适当的时候Bitmap的状态。系统oom之后，输出bitmap信息，便于查找问题。

```java
		// Raw height and width of image
        final int height = options.outHeight;
        final int width = options.outWidth;
        int inSampleSize = 1;

        if (height > reqHeight || width > reqWidth) {
            final int halfHeight = height / 2;
            final int halfWidth = width / 2;
            // Calculate the largest inSampleSize value that is a power of 2 and keeps both
            // height and width larger than the requested height and width.
            while ((halfHeight / inSampleSize) > reqHeight
                    && (halfWidth / inSampleSize) > reqWidth) {
                inSampleSize *= 2;
            }
        }
```

## 崩溃上报、分析
- 搜集更详细的信息，进程 线程 内存情况 页面 操作路径，特定场景下搜集网路 电量...

## 卡顿 线程优先级 CPU调度
- 线程优先级会影响Android系统的调度策略，当CPU繁忙的时候，线程调度会对执行效率有非常大的影响。避免存在高优先级线程空等低优先级线程，主线程等待后台线程的锁。
- 获取卡顿信息发送SigQuit信号，读取data/anr/trace 详细信息。

## 获取所有线程堆栈
- Thread.getAllStackTraces()  7.0不返回主线程的堆栈。

## 事件分发机制
```Java
	public boolean dispatchTouchEvent(MotionEvent ev){
		boolean consume = false;
		if (onInterceptTouchEvent(ev)) {
			consume = onTouchEvent(ev);
		}else{
			consume = child.dispatchTouchEvent(ev);
		}
		return consume;
	}
```
- onTouchListener的优先级高于OnTouchEvent

## ConstraintLayout 联动&Behavior

## View宽高
- onLayout以后才能确定拿到View的宽高，getMeasureWidth有可能不等与getWidth，源码上getWidth是mRight-mLeft。获取View宽高 1、onWindowFocusChanged 2、view.post() 源码解析：View源码中AttachInfo(附加到父View时为视图提供的一组信息)handler实现，运行在当前视图线程。

## ViewRoot WindowManager DecorView
- 在ViewRoot中requestlayout() 会检测当前线程是否为创建ViewRootImpl的线程，如果不是就会报出异常。viewRootImpl是在onResume时创建的，Android以此控制操作UI要在主线程中。Android是单线程模型，因为支持多线程修改View的话，容易出现线程同步，线程安全的问题，简化了系统设计。

## 渠道打包 自动化部署
- https://codezjx.com/2015/10/30/gradle-app-multi-flavor/

## 2020-04-01 11:11:03 @cly
- [BitmapRegionDecoder 区域解码器加载超大图](https://www.jianshu.com/p/878e4ddaa51b)

## 2020-04-08 10:30:05 @cly
- MAT The platform metadata area could not be written - 文件无写入权限。open -a mat.app --args -data /Users/bob/Documents/mat/heapDump 
- hprof-conv -z /Users/bob/Documents/mat/heapDump/memory-20200408T110315.hprof 1.hprof hporf文件转换

## 2020-04-08 22:39:26 @cly 设计模式
- 单例模式
- 装饰模式 file io context activity
- 建造者模式 okhttp源码
- 代理模式 动态代理 注解
- 享元模式 handler源码
- 适配器模式 
- 外观模式 门面模式 架构隔离
- 迭代器模式 容器中广泛应用
- 观察者模式 rxJava
- 责任链模式 okHttp/事件分发

- 创建型 结构型 行为型

## 2020-04-09 17:00:30 @cly












