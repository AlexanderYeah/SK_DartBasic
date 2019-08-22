Image Widget

#### 1 flutter 加载图片的方式

|    new Image    |      从ImageProvider 中获取图像       |
| :-------------: | :-----------------------------------: |
| new Image.asset |    使用key 从assetBundle 获取图片     |
|  Image.network  |           从网络中获取图片            |
|   Image.file    |          从本地文件获取图片           |
|  Image.memory   | 用来加载Uint8List资源（字节数组）图片 |



#### 2 image 支持的图片类型

JPEG PNG GIF Animated GIF 等等





#### 3 加载图片

加载本地的图片要在pubspec.yaml 中配置好,asset的一定要在flutte 下面的一级

```dart
# The following section is specific to Flutter.
flutter:

  # The following line ensures that the Material Icons font is
  # included with your application, so that you can use the icons in
  # the material Icons class.
  uses-material-design: true

  assets:
      - images/flutter.png
```



然后再去加载使用

> ​         Image.asset('images/flutter.png'),





