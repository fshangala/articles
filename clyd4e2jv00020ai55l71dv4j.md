---
title: "Cross-Platform Rest and WebSockets Client Application: Setup"
seoTitle: "Flutter: Cross-Platform REST and WebSockets App"
seoDescription: "Learn how to build a cross-platform Rest and WebSockets client app using Flutter, featuring go_router for efficient navigation"
datePublished: 2024-07-08T15:11:20.683Z
cuid: clyd4e2jv00020ai55l71dv4j
slug: cross-platform-rest-and-websockets-client-application-setup
ogImage: https://cdn.hashnode.com/res/hashnode/image/upload/v1720311710802/6d2edcb3-0c40-4447-a5d1-8632ddc32348.avif
tags: websockets, dart, flutter, apis, rest-api, httpclient

---

# Introduction

There are a lot of frameworks we can use to write this application. The choice of the programming language to use depends on what framework we decide is best suited to build the application.

With flutter we can have the same code-base compiled for all the platforms and it also easily gives us the access to the native code in case there is a native functionality we would like to implement.

# Initialization

We create a new flutter application using the command below.

```bash
flutter create --org com.fshangala.apps restapi_websockets_client && cd restapi_websockets_client
```

Our application requires some way of navigating across screens. The default way will work just fine, but it is going to be difficult for us to extract route parameters when we build for the web. The suitable solution to this problem is using go\_router.

We install go\_router using the command below.

```bash
flutter pub add go_router
```

We create a minimal implementation of the home screen at `lib/screens/home_screen.dart`

```dart
import 'package:flutter/material.dart';

class HomeScreen extends StatefulWidget {
  const HomeScreen({super.key});

  @override
  State<StatefulWidget> createState() {
    return HomeScreenState();
  }
}

class HomeScreenState extends State<HomeScreen> {
  @override
  Widget build(BuildContext context) {
    return Scaffold(
      appBar: AppBar(
        title: const Text("RestAPI WebSockets Client"),
      ),
    );
  }
}
```

We configure the router and add `HomeScreen` as the default route.

```dart
import 'package:flutter/material.dart';
import 'package:go_router/go_router.dart';
import 'package:restapi_websockets_client/screens/home_screen.dart';

void main() {
  runApp(const MyApp());
}

// GoRouter configuration
final _router = GoRouter(
  routes: [
    GoRoute(
      path: '/',
      builder: (context, state) => const HomeScreen(),
    ),
  ],
);

class MyApp extends StatelessWidget {
  const MyApp({super.key});

  // This widget is the root of your application.
  @override
  Widget build(BuildContext context) {
    return MaterialApp.router(
      routerConfig: _router,
      title: "RestAPI WebSockets Client",
      debugShowCheckedModeBanner: false,
    );
  }
}
```

This is what we have so far.

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1720230560257/9191dab4-d699-46ad-9e35-9e05104fa7eb.png align="center")