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














