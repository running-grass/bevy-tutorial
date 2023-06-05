# 调度器简介

Bevy 中的调度器用来编排所有系统的运行时间及运行顺序、运行条件。

## 相关术语

- 系统(System) 可以访问世界中的数据的常规函数的带状态实例
- 系统集(SystemSet)  系统(集)的逻辑分组
- 条件 返回值为`bool`类型的函数
- 依赖 指定系统(集)之间的先后关系
- 调度表 一张系统的运行图
- 调度 确定系统的运行时间和运行条件

## 系统集的定义

## 定义依赖

## 声明运行条件




0.10 版本的调度器进行了较大的改动。详见 [rfc](https://github.com/bevyengine/rfcs/blob/main/rfcs/45-stageless.md) 和 [迁移文档](https://bevyengine.org/learn/migration-guides/0.9-0.10/#migrate-engine-to-schedule-v3-stageless)
