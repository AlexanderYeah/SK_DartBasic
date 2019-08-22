### widget

在flutter 中，几乎所有的东西都是widget，本身是用户界面的基本构建快，将widget组成一个层次结构，

调用widget树。每一个窗口widget都嵌套在父窗口widget中，并且从其父窗口中继承属性。甚至应用程序对象本身也是一个组件，没有单独的应用程序对象。



widget可以定义 

* 结构元素 -- 按钮或者菜单
* 文体元素 -- 字体或者颜色主题
* 类似布局的填充或对齐的一个方向



1 显示Hello world

```dart
class MyApp extends StatelessWidget {
  // This widget is the root of your application.
  @override
  Widget build(BuildContext context) {
    return MaterialApp(
      title: 'SK DDDSKKS',
      theme: ThemeData(
        primarySwatch: Colors.blue,
      ),
      home: Scaffold(
        appBar: AppBar(
          title: Text("Alex Code"),
        ),
        body: Center(
          child: Text("Hello world"),
        ),
      ),
    );
  }
} 
```





2 项目结构

* 项目的名称

  * android  安卓相关工程文件
  * build 项目的构建输出目录
  * ios   ios 相关的部分工程文件
  * lib    项目中的dart 源文件
    * src 包含其他的源文件
    * main.dart 自动生成的项目入口文件

  * test  测试相关的文件
  * pubspec.ymal 项目依赖配置文件





3 归档图片资源和处理不同的分辨率

assets 文件夹

assets 文件夹 可以放到任何属性文件夹中，Flutter 并没有预先定义文件结构，在pubspec.ymal 中声明asset 的位置吗，然后flutter 会识别出来。



对应的分辨率放在不同的文件夹

images/home.png

images/2.0x/home.png

images/3.0x/home.png





4 归档stirng 资源 

将字段作为静态的字段保存在类中

```dart
class Strings {
  static String helloMsg = "Hello From Alexander";
}

Text(Strings.helloMsg)
    
```







