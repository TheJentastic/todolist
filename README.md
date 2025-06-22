# TODO-LIST

本项目是一个基于 Vue2 的单页面 TODO-LIST 应用，实现了以下功能：

- [ ] 创建TODO
- [ ] 删除TODO
- [ ] 编辑TODO

## 开发步骤

### 1. 初始化项目

```bash
npm install -g @vue/cli
vue create vue2-todolist
cd vue2-todolist
npm run serve
```

### 2. 编写主页面 `App.vue`

- 使用 `<template>`、`<script>` 和 `<style>` 结构。
- 数据结构：todos（数组，每个 todo 有 id、text、editing）。
- 方法：addTodo、deleteTodo、editTodo、saveEdit。

### 3. 实现功能

#### 创建 TODO

- 输入框输入内容，点击"添加"按钮，将新 todo 加入 todos 数组。

#### 删除 TODO

- 每个 todo 右侧有"删除"按钮，点击后从 todos 数组移除该项。

#### 编辑 TODO

- 每个 todo 右侧有"编辑"按钮，点击后该项变为可编辑状态，编辑完成后保存。

### 4. 启动项目

```bash
npm run serve
```

访问 http://localhost:8080 查看效果。
