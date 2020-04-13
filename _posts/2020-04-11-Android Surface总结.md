---
layout: post
title:  "SurfaceView"
date:   2020-04-11 10:59:21 +0700
categories: android,音视频
---
SurfaceView是一个拥有独立Surface的控件，由与拥有了独立的绘图单元，所以SurfaceView可以在其他线程中进行绘制，如图所示，图中DecorView中除了SurfaceView外都拥有同一个绘图表面，它们共同映射了Surface Flinger中的一个Layer, 而SurfaceView则映射到了下面的Layer, 可见SurfaceView在绘制的时候会被其他控件给挡住，因此Android用了一个办法来解决这个问题，那就是在将Activity对应的位置挖个洞，实际上就是在其宿主的Activity上设置一块透明区域。
 
  SurfaceView 特点
  1. 独立的绘制面板,因此可以在独立的线程中进行绘制
  2. 双缓冲

  GLSurfaceView是为了专门为使用OpenGL的控件，它拥有SurfaceView的特点

  SurfaceView的使用

  第一步，添加回调监听SurfaceView的生命周期
  {% highlight java %}
  mSurfaceHolder = getHolder();
  mSurfaceHolder.addCallback(this);
  {% endhighlight %}

  第二步, 在surfaceCreated中启动绘制线程
  {% highlight java %}
  @Override
  public void surfaceCreated(SurfaceHolder holder) {
      mDrawThread = new DrawThread();
      mDrawThread.start();
  }
  {% endhighlight %}

  第三步, 通过SurfaceHolde.lockCanvas获取Canvas，然后绘制，绘制完，调用unlockCanvasAndPost显示出来
  {% highlight java %}
  Canvas canvas = mSurfaceHolder.lockCanvas();
  // 使用canvas绘制内容 
  ...
  mSurfaceHolder.unlockCanvasAndPost(canvas);
  {% endhighlight %}
