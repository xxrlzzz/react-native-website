---
id: navigation
title: 使用导航器跳转页面
---

移动应用基本不会只由一个页面组成。管理多个页面的呈现、跳转的组件就是我们通常所说的导航器（navigator）。

本文档总结对比了 React Native 中现有的几个导航组件。如果你刚开始接触，那么直接选择[React Navigation](navigation.md#react-navigation)就好。 React Navigation 提供了简单易用的跨平台导航方案，在 iOS 和 Android 上都可以进行翻页式、tab 选项卡式和抽屉式的导航布局。

如果你想同时在 iOS 和 Android 上达到看起来像原生，或者你想把 RN 整合到一个已经有原生导航管理的 APP 里, 下面这个库提供了在两个平台都适用的原生导航: [react-native-navigation](https://github.com/wix/react-native-navigation).

## React Navigation

社区今后主推的方案是一个单独的导航库`react-navigation`，它的使用十分简单。React Navigation 中的视图是原生组件，同时用到了运行在原生线程上的`Animated`动画库，因而性能表现十分流畅。此外其动画形式和手势都非常便于定制。

要想详细了解 React Navigation 的具体用法，请访问其[官方网站](https://reactnavigation.org/)。
