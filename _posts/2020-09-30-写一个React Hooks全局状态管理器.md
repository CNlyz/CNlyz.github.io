---
title: 写一个React Hooks全局状态管理器
date: 2020-09-30 15:00:00 +0800
categories: [前端, React]
tags: [React, JavaScript]
---

# 写一个React Hooks全局状态管理器

最近在写一个mvp项目, 于是捡起了之前轻量体验过的**React Hooks**, 但是发现官方提供的**useReducer**和**useContext**有一些瓶颈(也有可能是我的使用姿势不对...), 主要在一下两点:
1. 这一点其实是用**Typescript**才会出现, 并且只是我个人感觉比较别扭。就是向**provider**组件传入**value**时, 没有比较优雅的办法将**dispatch**传进去, (当然可以在根状态里定义好**dispatch**, 如下图, 可我就是感觉很不爽)

![](../../assets/img/dispatch.png)

2. 如果用JavaScript写代码, 其实第一点不是问题, 因此真正的问题在第二点。当**context**里的某一个属性更新时, 会引起所有依赖这个**context**的组件都更新, 这也就意味着不依赖这个属性的组件也会更新, 显然这会导致一些性能问题。虽然可以通过拆分**context**来解决这个问题, 但是比较繁琐, 工程规模大了以后代码就比较难看了。

