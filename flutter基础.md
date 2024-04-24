# 功能整理





# 基础

## 1、版本错误，版本很多是老的



## 2、路径问题（一定要英文路径）





## 3、包下载、启动

```
flutter packages get
```

```
flutter run
```



## 4、flutter创建

```
flutter create weixin
```



## 5、命名规范问题

![image-20240322072638152](C:/Users/lingzipeng/AppData/Roaming/Typora/typora-user-images/image-20240322072638152.png)



## 6、图片自适应问题

```
fit: BoxFit.cover,
```

## 7、StatefulWidget和StatelessWidget的区别

`StatelessWidget` 是一个无状态的 Widget 类型，意味着它的 UI 在创建后就不会再发生变化。无状态的小部件，即在其生命周期内不会发生状态变化

- 如果你的 UI 不需要根据数据变化而更新，或者是静态的展示内容，可以使用 `StatelessWidget`。
- 如果你的 UI 需要根据数据变化或用户交互而更新，需要包含可变状态，就应该使用 `StatefulWidget`。

## 8、返回键

appbar自动生成

## 9、格式化代码快捷键

Android   Ctrl+ALT+L

vs    Shift+Alt+F

## 10、Widget状态管理

setState()

11、



## 100、其他

```
      - images/img.jpg
      - images/lebron.jpg
      - images/xk.jpg
      - images/a001.jpg
      - images/a002.jpg
      - images/a003.jpg
      - images/a004.jpg
      - images/a005.jpg
      - assets/tabbar_contacts@3x.png
      - assets/tabbar_contactsHL@3x.png
      - assets/tabbar_discover@3x.png
      - assets/tabbar_discoverHL@3x.png
      - assets/tabbar_mainframe@3x.png
      - assets/tabbar_mainframeHL@3x.png
      - assets/tabbar_me@3x.png
      - assets/tabbar_meHL@3x.png
      - assets/haugnbo.png
      - images/ff_IconShowAlbum@3x.png
      - images/ff_IconQRCode@3x.png
      - images/ff_IconShake@3x.png
      - images/ff_IconBrowse1@3x.png
      - images/ff_IconSearch1@3x.png
      - images/ff_IconBottle@3x.png
      - images/ff_IconNearby@3x.png
      - images/GameCenterH5GameMenuBtn@2x.png
      - images/PaidDetail_MiniProgram@3x.png
      - images/arrow_ico@3x.png
      - images/AlbumHBSmallArror_Golden@2x.png
      - images/Card_ArrowGrey@2x.png
      - images/arrowOnclick_ico@2x.png
      - images/Shake_icon_cardPackHL@2x.png
      - images/MoreMyFavorites@2x.png
      - images/MyCardPackageIcon@2x.png
      - images/MoreExpressionShops@2x.png
      - images/MoreMyAlbum@2x.png
      - images/MoreSetting@2x.png
      - images/add_friend_icon_addgroup@2x.png
      - images/add_friend_icon_offical@2x.png
      - images/Contact_icon_ContactTag@2x.png
      - images/plugins_FriendNotify@2x.png
      - images/刘备.png
      - images/曹操.png
      - images/孙权.png
      - images/关羽.png
      - images/张飞.png
      - images/吕布.png
      - images/赵云.png
      - images/诸葛亮.png
      - images/周瑜.png
      - images/鲁肃.png
      - images/司马懿.png
      - images/袁绍.png
      - images/华佗.png
      - images/华雄.png
      - images/公孙瓒.png
      - images/刘表.png
      - images/典韦.png
      - images/黄忠.png
      - images/刘禅.png
      - images/徐庶.png
      - images/郭嘉.png
      - images/荀攸.png
      - images/xiaoheizi.jpg
```

```
import 'package:dio/dio.dart';
import 'package:flutter/material.dart';

import 'test/a.dart';

class XKTabBar extends StatefulWidget {
  final String title;

  const XKTabBar({required this.title, Key? key}) : super(key: key);

  @override
  _XKTabBar createState() => _XKTabBar();
}

class _XKTabBar extends State<XKTabBar> {
  Dio dio = Dio();
  TextEditingController textController = TextEditingController();
  String responseData = '';

  void sendPostRequest() async {
    try {
      // 构建请求体
      Map<String, dynamic> data = {
        'username': "lihua",
        'password': '1234567',
      };

      Uri uri = Uri(
        scheme: 'http',
        host: 'localhost',
        port: 8080,
        path: '/user/login',
        queryParameters: data,
      );

      String url = uri.toString();

      // 发送POST请求
      Response response = await dio.post(url);

      // 处理服务器响应

      responseData = response.data.toString();

      print('成功: $responseData');
    } catch (e) {
      print('失败: $e');
    }
  }

  void sendGetRequest() async {
    try {
      // 发送GET请求
      Response response =
          await dio.get('http://127.0.0.1:4523/m1/3535579-0-default/test/a');

      responseData = response.data.toString();

      print('成功: $responseData');
    } catch (e) {
      print('失败: $e');
    }
  }

  @override
  Widget build(BuildContext context) {
    return Scaffold(
        appBar: AppBar(
          title: Text(widget.title),
          backgroundColor: const Color.fromARGB(255, 234, 230, 230),
        ),
        body: Container(
            alignment: const Alignment(0.0, 0.0),
            height: 100.0,
            child: ElevatedButton(
              onPressed: () {
                sendPostRequest();
              },
              child: const Text("老铁666"),
            )));
  }
}

```

