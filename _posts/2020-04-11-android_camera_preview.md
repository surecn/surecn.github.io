---
layout: post
title:  "SurfaceView与GLSurfaceView"
date:   2020-04-11 10:59:21 +0700
categories: android,音视频
---
  SurfaceView 特点
  1. 独立的绘制面板
  2. 双缓冲

  SurfaceView是一个拥有独立Surface的控件，由与拥有了独立的绘图单元，所以SurfaceView可以在其他线程中进行绘制，如图所示，图中DecorView中除了SurfaceView外都拥有同一个绘图表面，它们共同映射了Surface Flinger中的一个Layer, 而SurfaceView则映射到了下面的Layer, 可见SurfaceView在绘制的时候会被其他控件给挡住，因此Android用了一个办法来解决这个问题，那就是在将Activity对应的位置挖个洞，实际上就是在其宿主的Activity上设置一块透明区域。

