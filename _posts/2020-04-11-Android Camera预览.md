---
layout: post
title:  "Android Camera预览"
date:   2020-04-11 10:59:21 +0700
categories: android,音视频
---

  第一步，添加权限
  {% highlight xml %}
  <uses-permission android:name="android.permission.CAMERA"/>
  {% endhighlight %}

  第二步, 创建SurfaceView控件,并且在surfaceCreated和Activity.onResume方法中打开相机

  第三步, 调用Camera.open打开相机并设置相关参数
    {% highlight java %}
  mCamera = Camera.open(Camera.CameraInfo.CAMERA_FACING_FRONT);
  Camera.Parameters parameters = mCamera.getParameters();
  parameters.set("orientation", "portrait");
  //parameters.setFocusMode(Camera.Parameters.FOCUS_MODE_CONTINUOUS_VIDEO);
  List<Camera.Size> sizes = parameters.getSupportedPreviewSizes();
  for(Camera.Size size :sizes){
      parameters.setPreviewSize(size.width, size.height);
      mWidth = size.width;
      mHeight = size.height;
      break;
  }
  mCamera.setDisplayOrientation(90);
  mCamera.setParameters(parameters);
  parameters.setPreviewFormat(ImageFormat.NV21);

  mCamera.setPreviewCallback(new Camera.PreviewCallback() {
      @Override
      public void onPreviewFrame(byte[] data, Camera camera) {
          videoEncoder.putVideoData(data);
      }
  });
  {% endhighlight %}

  第四步, 在surfaceChanged中开始预览
  {% highlight java %}
  mCamera.setPreviewDisplay(holder);
  mCamera.startPreview();
  {% endhighlight %}
  

 