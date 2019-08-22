#### Widget 

Flutter 中的view 就是widget

1 无状态和有状态的Widget

StateslessWidgets  适用于用户界面不依赖于用户的信息的时候
StatesfulWidgets 有状态的，例如HTTP 网络请求或者用户交互之后收到数据动态表更新UI



 这就是一个无状态的Widget

```dart
Text("we like bom",
          style: new TextStyle(fontWeight: FontWeight.bold,
          fontSize: 55
          )
```





2 在Flutter 中通过widget 树来声明布局。

一个带有样式的按钮

```dart
        body: Center(
          child: MaterialButton(onPressed: (){
              print("Btn Click");
          },
          child: Text("Click Me"),
          padding: EdgeInsets.only(left: 25,right: 25),          
          ),
```



3 动态添加和删除组件

传入一个函数的表达式，来动态的进行widget 切换



4 如何给widget 来做动画

AnimationController 是一个可以暂停 寻找，停止，反转动画的Anamation 类型。

需要一个Ticker 当vsync 发生是来发送信号，并且在每一帧运行时创建一个	介于0-1之间的线性插值，可以创建一个或者多个Animation 并且附加给controller。





5 如何进行绘图

CustomPaint 和 CustomPainter 实现绘图的效果

```dart
import 'package:flutter/cupertino.dart';
import 'package:flutter/material.dart';

void main() => runApp(MyApp());

class MyApp extends StatelessWidget {
  // This widget is the root of your application.
  @override
  Widget build(BuildContext context) {
    return MaterialApp(
      title: 'SK DDDSKKS',
      theme: ThemeData(
        primarySwatch: Colors.blue,
      ),
      home: _MyCanvas(),   
    );
  }
}


// 创建一个类 继承自   CustomPainter
class MyCanvasPainter extends CustomPainter{

    @override
    void paint(Canvas cans,Size size){
        // 1 绘制一个圆形
        Paint paint = Paint();
        paint.color = Color.fromARGB(200, 150, 10, 1);
        cans.drawCircle(Offset(100,200), 50, paint);     

        // 2 绘制一个方形
        Paint paint2 = Paint();
        paint2.color = Color.fromARGB(60, 200, 15, 1);
        // 第一点位 左上角 第二个点位 右下角
        Rect rect = Rect.fromPoints(Offset(50,300), Offset(350,500));
        cans.drawRect(rect, paint2);
        
    }
    bool shouldRepaint(MyCanvasPainter oldDelegate) {
      return false;
    }
    bool shouldRebuildSemantics(MyCanvasPainter oldDelegate) {
      return false;
    }

}

class _MyCanvas extends StatelessWidget{
    @override
    Widget build(BuildContext context) {
      // TODO: implement build
      return Scaffold(
        body: CustomPaint(painter: MyCanvasPainter(),),
      );
  }

}


 
```





6 构建自定义的widgets

在Flutter 中 遇见组合多个小的widgets 来构建一个新的自定义的widgets

```dart
// 创建一个新的按钮

class SKButton extends StatelessWidget{
   final String lable;
   SKButton(this.lable);


  @override
  Widget build(BuildContext context) {
    return new RaisedButton(onPressed: (){
      print("Click me");
    },
    child: new Text(lable),
    );
  }

  
}

class _MyCanvas extends StatelessWidget{
    @override
    Widget build(BuildContext context) {
      // TODO: implement build
      return Scaffold(
        body: SKButton("这是我的按钮"),
        );
  
  }

}

```





