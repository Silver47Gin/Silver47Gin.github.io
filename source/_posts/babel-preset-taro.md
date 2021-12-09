---
title: babel-preset-taro
date: 2021-12-01 10:41:08
tags:
---

|    语言    |     选项      |                    配置                     |      备注      |
| :--------: | :-----------: | :-----------------------------------------: | :------------: |
|   react    |     默认      |             @babel/preset-react             |                |
|            | h5 hot reload |             react-refresh/babel             |                |
|    nerv    |     默认      |             @babel/preset-react             |                |
|    vue     |     默认      |            @vue/babel-preset-jsx            |                |
|    vue3    |     默认      |            @vue/babel-plugin-jsx            |                |
| typescript |    default    |          @babel/preset-typescript           | 读取 option.ts |
|            |  react/nerv   |        config.jsxPragma = moduleName        |                |
|            |   vue/vue3    | @babel/preset-typescript ,include: /\.vue$/ |                |
|     h5     |     默认      |       babel-plugin-transform-taroapi        |                |
|  default   |     默认      |              @babel/preset-env              |                |
|            |               |      @babel/plugin-proposal-decorators      |                |
|            |               |   @babel/plugin-proposal-class-properties   |                |
|            |               |       @babel/plugin-transform-runtime       |                |
|            |               |      babel-plugin-dynamic-import-node       |                |
