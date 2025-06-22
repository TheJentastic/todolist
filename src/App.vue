<template>
  <div>
    <!-- 头部输入框 -->
    <MyHeader @add-todo="addTodo" />
    <!-- 任务列表 -->
    <MyList
      :todos="todos"
      @toggle-complete="toggleComplete"
      @delete-todo="deleteTodo"
      @edit-todo="editTodo"
      @save-edit="saveEdit"
    />
    <!-- 底部统计和操作 -->
    <MyFooter
      :completedCount="completedCount"
      :totalCount="todos.length"
      :isAllCompleted="isAllCompleted"
      @toggle-all="toggleAll"
      @clear-completed="clearCompleted"
    />
  </div>
</template>

<script>
import MyHeader from './componets/MyHeader.vue';
import MyList from './componets/MyList.vue';
import MyFooter from './componets/MyFooter.vue';

export default {
  name: 'App',
  components: {
    MyHeader,
    MyList,
    MyFooter
  },
  data() {
    return {
      todos: [
        { id: 1, text: '抽烟', completed: false, editing: false },
        { id: 2, text: '喝酒', completed: false, editing: false },
        { id: 3, text: '开车', completed: false, editing: false }
      ]
    };
  },
  computed: {
    completedCount() {
      return this.todos.filter(t => t.completed).length;
    },
    isAllCompleted() {
      return this.todos.length > 0 && this.todos.every(t => t.completed);
    }
  },
  methods: {
    addTodo(text) {
      this.todos.push({
        id: Date.now(),
        text,
        completed: false,
        editing: false
      });
    },
    toggleComplete(id) {
      const todo = this.todos.find(t => t.id === id);
      if (todo) todo.completed = !todo.completed;
    },
    deleteTodo(id) {
      this.todos = this.todos.filter(t => t.id !== id);
    },
    editTodo(id) {
      this.todos.forEach(t => t.editing = false);
      const todo = this.todos.find(t => t.id === id);
      if (todo) todo.editing = true;
    },
    saveEdit(editedTodo) {
      const todo = this.todos.find(t => t.id === editedTodo.id);
      if (todo) {
        todo.text = editedTodo.text;
        todo.editing = false;
      }
    },
    toggleAll(checked) {
      this.todos.forEach(t => t.completed = checked);
    },
    clearCompleted() {
      this.todos = this.todos.filter(t => !t.completed);
    }
  }
};
</script>

<style>
body {
  background: #fafbfc;
}
#app {
  width: 500px;
  margin: 40px auto; /* 设置上下外边距为 40px，左右外边距为 auto，实现水平居中 */
  font-family: Arial, sans-serif;
  border: 1px solid #ccc; /* 将边框颜色改为浅灰色 */
  border-radius: 8px;
  overflow: hidden;
}
</style>

