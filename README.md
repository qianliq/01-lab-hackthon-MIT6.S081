# 01-lab-hackthon
Repo to store 2025 Hackthon contest entries.

> Ask: samuka007@dragonos.org

## 背景

关键词：operating system, computer network

提供给大家一个学习的机会和契机，鼓励大家尝试自己尚未有机会开始接触的lab！

## 规定

- 1 人一组，完成Lab任务
- 最终lab学习成果及文档需要提交 PR 到当前仓库
  或提交至 https://gitea.scutosc.cn/ 并发送邮件告知评委
- 选择 DragonOS 系的题目有加分

## 综合评分细则

1. 创新性与难度（25%）
   1. 完成的实验难度
   2. 实验的新颖度
   3. 对现实问题的指导意义
2. 功能完备性（55%）
   1. 完成了实验 / 实现了预期功能（35%）
   2. 需要实践测试
      1. 实践有启发性，实践的可复现性、应用性（15%）
   3. 需要写代码的
      1. 运行性能（10%）
      2. 代码质量（5%）
3. 展示效果（20%）
   1. 文档展示
   2. 路演效果

## 操作系统方向

### 6.S081

#### 背景

麻省理工学院大名鼎鼎的 PDOS 实验室开设的面向MIT本科生的操作系统课程。

#### 任务

参考：

- https://csdiy.wiki/%E6%93%8D%E4%BD%9C%E7%B3%BB%E7%BB%9F/MIT6.S081/

- https://pdos.csail.mit.edu/6.828/2021/schedule.html

> [!NOTE]
> 要求：完成两个及以上的 Lab 题目

题目见绿色 Assignment 字体后的链接
![题目见绿色 Assignment 字体后的链接](https://github.com/user-attachments/assets/c348efcb-1c71-4472-bf03-e487aee96ce1)


### DragonOS 系统调用 & 修复

#### 背景

DragonOS 是使用 Rust 编写的，以 Linux 架构作为参考的操作系统。

Repo: https://github.com/DragonOS-Community/DragonOS

当前 DragonOS 内，有不少系统调用，由于各种原因 ( C 与 Rust 语言差异等 ) ，导致调用时常不符合语义/行为不一致。

#### 任务

- 参考 https://bbs.dragonos.org.cn/t/topic/460 （以及最新引入的系统调用注册表，参考https://github.com/DragonOS-Community/DragonOS/pull/1164）在 DragonOS 内添加一个新的系统调用，并在用户态成功调用
- 寻找内核中行为与预期有出入的系统调用，建议寻找静态、接口不一致的错误

#### 参考

一个内核中静态分析得出行为不一致的 Shutdown 错误：

https://github.com/DragonOS-Community/DragonOS/issues/887

## 网络方向

### CS144

#### 背景
CS144 通过提前为网卡硬件、TCP 等组件定义抽象，提供了一套精巧设计的框架，为同学们理解网络模型提供了恰到好处的“题目”，
即，通过框架可以一窥整个计算机网络实现的意图与设计，又得以从重复的工作中抽离出来，将时间投入到理解网络模型与底层原理
当中来。

#### 任务
https://csdiy.wiki/%E8%AE%A1%E7%AE%97%E6%9C%BA%E7%BD%91%E7%BB%9C/CS144/

努力完成一个 TCP 协议栈吧！
- 实现至 checkpoint 3 及以上

### DragonOS Socket

#### 背景

DragonOS 网络子系统中，Inet 协议簇依赖于 [smoltcp] 库实现。
在Repo https://github.com/Samuka007/dragonos-berkeley-socket 中将网络子系统相关
的框架实现抽离了出来，基于 tap 设备与 Linux Epoll 机制模拟中断，允许在用户空间测试
[`Inet 协议簇`](https://github.com/Samuka007/dragonos-berkeley-socket/tree/master/src/socket/inet) 
的功能。

#### 任务

目前实现的协议栈涉及TCP多层状态机的转换，由于 Rust 的借用机制，以及 [smoltcp] 的 Socket 接口不完全与
Berkeley 定义相一致，因此实现上会出现一些冗余的情况，让各层状态机之间的转换变得复杂。

本实验的任务是尝试基于已有的网卡抽象，参考现有的 Inet 协议簇 实现，基于 [smoltcp] 自己实现 TCP Socket，
并尝试在现有的 TCP 实现上予以优化。

## 其他方向

自选实验，需要体现技术栈深度


[smoltcp]: https://crates.io/crates/smoltcp
