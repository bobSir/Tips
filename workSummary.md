# Android

## 高级UI
- 事件分发
- view渲染机制
- 常用View
- 自定义 View layoutManager

## 组件内核
- activity与调用栈
- fragment
- service
- 组件通信

## IPC
- 跨进程通信
- binder机制

## 数据持久化
- 文件
- kv sharedPreference  MMKV
- sqlite

## framework
- xms  -- ams  wms
- handler消息机制


# 性能优化

## 用户角度性能感官
- 启动
- UI 
- 跳转
- 响应

## UI显示流程&原理
- 应用层 绘制 measure layout draw -> suface缓存数据通过surfaceFliger交由系统层渲染，通过android刷新机制刷新绘制

## 根本原因 出发点
- UI  布局嵌套 ，页面控件太多>80， 刷新不合理
- 数据  主线程被阻塞，数据处理cpu占用高主线程抢占不到时间片，内存管理导致抖动gc

## 分析工具
- systrace UI卡顿问题 启动流程 锁性能
- profile 
- traceView
- MAT

## 布局优化
- 布局嵌套
- 过度绘制
- include  merge  viewStub 自定义view
- 硬件加速 view.setLayerType(View.LAYER_TYPE_HARDWARE,null)  结束设置为none，内存申请消耗 不能及时回收

## 崩溃分析
- 统计 收集 上报
- 点到面分析 预防
- 高性能编码习惯
- 判null @nullable注释
- 架构规范
- A/B test 兜底 自动降级

## 内存优化
- profile MAT 检测 定位
- 内存泄漏 内存溢出
- 内存抖动

## 启动优化
- 体验优化 设置背景主题
- 减少application onCreate 耗时操作 调整时机 任务分优先级
- 检查进程 一个进程application onCreate 执行一次 判断进程

## apk体积优化 aar体积优化
- lint 
- 混淆
- 资源优化
- 统一API

## 网络优化
- 缓存
- 接口聚合

## 耗电优化

-  

## 体验优化
- 业务推动力
- 竞品维度分析

## 稳定性优化
- 高性能编码
- 设计模式
- crash监控
- ANR分析

# 混合开发

## 跨平台

### RN
-  react设计模式 jsCore 原生渲染 上手难度高 facebook核心维护项目 三方支持库多

### weex
- vue设计模式 原生渲染 JsBridge Render DOM 上手容易 社区环境不好 很多需要原生拓展支持 与跨平台背道而驰

### fluter
- google出品 dart 原生渲染 frameWork Engine weiget canvans 性能高

### hybrid
- webView
- js-native交互 通信框架
- native 赋予前端原生能力

### 静态信息动态化展示方案
- 弱交互视图展示，单纯视图表达产品需求
- json描述视图 原生创建&渲染
- 自定义DSL

## 热更新
- 开发模式 流程
- 测试模式 流程
- 环境配置
- 更新策略 秒开 及时
- 版本控制

# 架构
- 设计模式
- 代码规范
- 重构
- 架构在于‘治’，检测在于‘防’

# 产品理解
- 利用自己的知识体系抽象业务 -> 构建架构 代码结构 -> 完成需求
- 维度分析业务&技术壁垒

# 管理
- aar私有库 jks 自动化工作流
- 业务推动力
- 技术影响力
- 团队影响力

# 职业规划
-  



