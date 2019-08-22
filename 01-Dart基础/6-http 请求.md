http 请求

使用http package 进行网络请求操作



#### 1 安装步骤

* Step1 

  在pubspec.yaml 文件中添加依赖

  ```dart
  dependencies:
    http: ^0.12.0+1
  ```


* Step2

  ```shell
   flutter packages get
  ```



* Step3 

  导入头文件

  > import 'package:http/http.dart' as http;





#### 2 使用

```dart
 	
          var responseBody;
          http.Response response =  await http.get(url);
          
          if (response.statusCode == 200){
              responseBody = json.decode(response.body);
              replyTo.send(responseBody);
          }else{
              print("error happend");
          }
```





### 3  添加一个进度条

flutter 中的一个widget叫做ProgressIndicator ,通过一个布尔值来控制是否展示进度	，在任务开始的时候，告诉Flutter 更新状态，在结束后进行隐藏。



```dart
import 'dart:io';

import 'package:flutter/cupertino.dart';
import 'package:flutter/material.dart';
import 'package:flutter/widgets.dart';

import 'dart:convert';
void main() => runApp(MyApp());

class MyApp extends StatelessWidget {
  // This widget is the root of your application.

  @override
  Widget build(BuildContext context) {
    return MaterialApp(
      theme: ThemeData(
        primarySwatch: Colors.blue,
      ),
      home: SampleAppPage(),

    );
  }
}

class SampleAppPage extends StatefulWidget{
    SampleAppPage({Key key}) : super(key:key);
    @override
    _SampleAppPageState createState() =>  _SampleAppPageState();
    
}

class _SampleAppPageState extends State<SampleAppPage>
{
    List widgets =[]; 
   // 加载数据
    dataHandle()async{

        String url = "https://www.apiopen.top/journalismApi";
        var responseBody;
        var http = new HttpClient();
        var request = await http.getUrl(Uri.parse(url));
        var response = await request.close();
        if (response.statusCode == 200){
          print("Success");
          responseBody = await response.transform(utf8.decoder).join();
          responseBody = json.decode(responseBody);
          // 通过调用setState 方式来更新UI
          setState(() {
            widgets = responseBody["data"]["tech"];
            print(widgets.length);
          });   
        }else{
          print("error happend");
        }
    }



    // 初始化状态的时候加载数据
    @override
    void initState() {
        super.initState();
        dataHandle();
    }

    Widget getRow (int idx){
        return Padding(
            padding: EdgeInsets.all(10),
            child: Text("${widgets[idx]["title"]}",
            style: new TextStyle(fontSize: 22,color: Colors.green),),
        );
    }

    // 是否展示指示器的标记
    isShow(){
      return widgets.length == 0;
    }


    // 获取页面的body
    getBody(){
      if(isShow()){
        return  getProgressIndicator();
      }else{
        return getListView();
      }
    }

    // 创建列表
    ListView getListView() => ListView.builder(
      itemCount: widgets.length,
      itemBuilder: (BuildContext context,int idx){
        return getRow(idx);
      },
    );

    // 创建一个进度指示
    getProgressIndicator(){
      return Center(child: CircularProgressIndicator());
    }


    @override 
    Widget build(BuildContext context){

      return Scaffold(
          appBar: AppBar(title: new Text("Hello World")),
          body: getBody(),
      );
    }
}



 

```



