---
title: react-native-auto-link
date: 2021-12-01 15:38:46
tags:
---

### 如何运作

每个平台有自己的平台设置。他指示 CLI 如何找到原生依赖的相关信息。这些信息通过`config`命令在 JSON 文件中暴露出来。这之后被脚本通过平台特定的构建工具使用。脚本应用其中的逻辑来链接原生的特定代码到对应平台。

## iOS 平台

Podfile 所需的 native_modules.rb 脚本在安装阶段从 react-native 配置中获取包元数据，并且：

- 通过 CocoaPods 添加依赖。
- 添加`build phase`脚本到应用的`build phase`

这意味着所有的库必须在根目录或者 Xcode 项目位置提供`Podspec`。`Podspec`会指向应用使用的原生代码。

这种实现可以保证一个库只被引入一次。如果开发者需要直接自定义`pod`,请将其包含在`use_native_modules!`函数上。

- `native_modules.rb`文件的作用是找到所有的 ios 原生模块，并且使用`pod`安装依赖

## android 平台

`native_modules.gradle`脚本被包含在项目的`settings.gradle`和`app/build.gradle`文件中：

1. 在构建时，在构建脚本运行之前：

- 第一个 Gradle 插件(在`settings.gradle`中)运行`applyNativeModulesSettingsGradle`方法。这会从`react-native config`读取包的标签信息，来添加安卓项目。
- 第二个 Gradle 插件(在`app/build.gradle`中)运行`applyNativeModulesAppBuildGradle`方法。这会生成一系列的 RN 包，用于生成`/android/build/generated/rn/src/main/java/com/facebook/react/PackageList.java`文件。

2. 在运行时，上面步骤生成的 RN 包，会被`MainApplication.java`中的`ReactNativeHost`的`getPackages`方法注册

- 如果开发者想覆盖`MainReactPackage`的配置，开发者可以传递一个可选的`MainPackageConfig`在初始化`PackageList`的时候。
