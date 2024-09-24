---
title: 🟢 Crud 应用
description: 挑战 5 是关于重构 CRUD 应用程序
author: thomas-laforge
contributors:
  - tomalaforge
  - tomer953
  - svenson95
  - jdegand
  - LMFinney
  - enochgao
challengeNumber: 5
command: angular-crud-application
sidebar:
  order: 2
---

## 信息

与后端进行通信并保持全局/本地状态同步是任何应用程序的核心。您将需要掌握以下最佳实践来构建强大且可靠的 Angular 应用程序。

## 声明

在本练习中，您有一个小型 CRUD 应用程序，它获取 TODOS 列表、更新和删除一些待办事项。

目前，我们有一个有效的示例，但充满了很多不好的做法。

### 第 1 步：使用最佳实践进行重构

你需要做的是:

- 避免使用**any**作为类型。使用接口来利用Typescript的类型系统以防止错误。
- 使用**隔离的服务**来处理所有HTTP请求，并使用**Signal**来管理您的待办事项列表。
- 不要**改变**数据。

```typescript
// 避免这种情况
this.todos[todoUpdated.id - 1] = todoUpdated;

// 最好采用类似的方式，但需要改进，因为我们仍然希望保持相同的顺序。
this.todos = [...this.todos.filter((t) => t.id !== todoUpdated.id), todoUpdated];
```

### 第 2 步: 改进

- 添加一个 **删除** 按钮: _<a href="https://jsonplaceholder.typicode.com/" target="_blank">伪造 API文档</a>_
- 正确处理 **错误**. _(全局的)_
- 添加一个全局的 **加载** 指示器. _你可以使用 MatProgressSpinnerModule_

### 第 3 步: 可维护性!! 添加一些测试

- 添加 2/3 的单元测试.

### 第 4 步: 太棒了!!! 管理你的状态.

- 使用 **component store of ngrx**, **ngrx/store**, **rxAngular**, **tanstack-query** 或者 **ngrx/signal-store** 作为你组件本地状态存储.
- 添加一个**本地化的**加载/错误指示器，例如仅在正在处理的待办事项上显示，并**禁用**所有已处理待办事项的按钮。_(提示: 您需要创建一个ItemComponent组件)_
