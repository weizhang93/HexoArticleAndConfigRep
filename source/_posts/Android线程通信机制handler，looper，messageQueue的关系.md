---
title: Android线程通信机制handler，looper，messageQueue的关系
date: 2016-05-19 
tags: Android
photos: 
- 
---

Android应用程序是单线程模型的，（注意，此单线程模型并不是指一个应用程序里只有一个线程，而是说这个程序围绕着一个主要的线程)当启动一个应用程序，android会自动创建一个main线程，也叫UI线程。这个线程负责事件的分发以及屏幕的绘制，是一个很重要的线程。

UI线程是线程不安全的，我想可能是android想避免多个线程对屏幕上的数据操作带来的数据混乱的问题，所以只让UI线程操作屏幕上的数据。如果UI线程在操作后都5S没有响应的话，会直接报出Application Not Respond(即ANR)错误(长时间不响应会带来很差的用户体验)。但是耗时的业务逻辑处理又是不可避免的，如大量图片的加载，网络请求等，这些耗时的操作势必不能放在UI线程里。我们必须新开线程来处理。结合前面的线程不安全，您联想到什么没有？有没有一种机制让普通线程把处理结果发送给UI线程呢？

当当当，Handler出场了。伴随Handler的，还有Looper和MessageQueue，Message三位。这四位便组成了android应用程序线程间通信机制。大概流程是这样的，Handler传递Message给MessageQueue，MessageQueue将Message放进它的队列，这时候在UI线程的Looper会不断轮询MessageQueue，取出里面的Message分发或者处理。嗯，就是这样。不要逗我了，普通线程呢，被狗吃辣？客官莫急，待我慢慢道来。

我们一般在Activity这些组件里定义Handler时，此时Handler便是在UI线程里，取得的Looper也是UI线程的Looper，这时候新开一个普通线程，在这个线程里使用mHandler.sendMessage(new Message()) or mHandler.post(new Runnable()),结果便是放在Message或者Runnable里（Runnable会被Handler自
动转换为Message），这就是整个过程。来一幅图以便理解。

![图片](http://img.blog.csdn.net/20160318162514853)

下面是Handler主要调用的构造函数。

```java
public Handler(Callback callback, boolean async) {
        ...
        mLooper = Looper.myLooper();
        if (mLooper == null) {
            throw new RuntimeException(
                "Can't create handler inside thread that has not called Looper.prepare()");
        }
        mQueue = mLooper.mQueue;
        mCallback = callback;
        mAsynchronous = async;
    }
```

