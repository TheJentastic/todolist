<template>
  <div class="item-row">
    <!-- 复选框：切换任务完成状态 -->
    <input type="checkbox" :checked="todo.completed" @change="toggleComplete" />
    <!-- 任务名或编辑框 -->
    <span v-if="!todo.editing" @dblclick="editTodo">{{ todo.text }}</span>
    <input
      v-else
      v-model="editText"
      @keyup.enter="saveEdit"
      @blur="saveEdit"
      class="edit-input"
    />
    <!-- 编辑按钮 -->
    <button v-if="!todo.editing" @click="editTodo">编辑</button>
    <!-- 保存按钮 -->
    <button v-if="todo.editing" @click="saveEdit">保存</button>
    <!-- 删除按钮 -->
    <button @click="deleteTodo">删除</button>
  </div>
</template>

<script>
export default {
  name: 'MyItem',
  props: {
    todo: {
      type: Object,
      required: true
    }
  },
  data() {
    return {
      editText: this.todo.text
    };
  },
  watch: {
    todo: {
      handler(newVal) {
        this.editText = newVal.text;
      },
      deep: true
    }
  },
  methods: {
    toggleComplete() {
      this.$emit('toggle-complete', this.todo.id);
    },
    deleteTodo() {
      // 弹出确认框，如果用户点击确定，则触发删除事件
      if (confirm('确定删除吗？')) {
        this.$emit('delete-todo', this.todo.id);
      }
    },
    editTodo() {
      this.$emit('edit-todo', this.todo.id);
    },
    saveEdit() {
      this.$emit('save-edit', { ...this.todo, text: this.editText });
    }
  }
};
</script>

<style scoped>
.item-row {
  display: flex;
  align-items: center;
  margin: 10px 0;
  padding: 5px;
  transition: background-color 0.3s ease; /* 添加过渡效果，让背景变化更平滑 */
}
.item-row:hover { /* 鼠标悬停时的样式 */
  background-color: #f5f5f5; /* 灰色背景 */
}
.item-row input[type="checkbox"] {
  margin-right: 10px;
}
.item-row .edit-input {
  margin-right: 10px;
  flex: 1;
}
.item-row button {
  margin-left: 5px;
}
</style>
