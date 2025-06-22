<template>
  <section class="list-section">
    <!-- 遍历 todos，渲染每一项任务 -->
    <MyItem
      v-for="todo in todos"
      :key="todo.id"
      :todo="todo"
      @toggle-complete="$emit('toggle-complete', todo.id)"
      @delete-todo="$emit('delete-todo', todo.id)"
      @edit-todo="$emit('edit-todo', todo.id)"
      @save-edit="$emit('save-edit', $event)"
    />
  </section>
</template>

<script>
import MyItem from './MyItem.vue';
export default {
  name: 'MyList',
  components: { MyItem },
  props: {
    todos: {
      type: Array,
      required: true
    }
  }
};
</script>

<style scoped>
.list-section {
  width: 500px;
  background: #fff;
  padding: 10px;
  border-radius: 6px;
  margin: 20px 0;
}
</style>
