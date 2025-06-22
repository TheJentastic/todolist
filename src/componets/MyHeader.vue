<template>
  <header class="header">
    <!-- 任务输入框，按回车添加任务 -->
    <input
      v-model="inputValue"
      @keyup.enter="addTodo"
      type="text"
      placeholder="请输入你的任务名称，按回车键确认"
      class="todo-input"
    />
    <!-- 这里没有单独的添加按钮，回车即添加，可根据需要添加按钮 -->
  </header>
</template>

<script>
export default {
  name: 'MyHeader',
  data() {
    return {
      inputValue: '' // 输入框内容
    };
  },
  methods: {
    addTodo() {
      // 输入内容为空不添加
      if (!this.inputValue.trim()) return;
      // 触发自定义事件，通知父组件添加任务
      this.$emit('add-todo', this.inputValue.trim());
      this.inputValue = '';
    }
  }
};
</script>

<style scoped>
.header {
  padding: 20px;
}
.todo-input {
  width: 500px;
  padding: 10px;
  font-size: 16px;
  box-sizing: border-box;
}
</style>
