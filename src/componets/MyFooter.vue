<template>
  <footer class="footer">
    <!-- 左侧区域：全选复选框和统计文本 -->
    <div class="footer-left">
      <!-- 全选复选框 -->
      <input type="checkbox" :checked="isAllCompleted" @change="$emit('toggle-all', $event.target.checked)" />
      <!-- 统计文本 -->
      <span> 已完成{{ completedCount }} / 全部{{ totalCount }} </span>
    </div>
    <!-- 右侧区域：清除已完成任务按钮 -->
    <button class="clear-btn" @click="$emit('clear-completed')">清除已完成任务</button>
  </footer>
</template>

<script>
export default {
  name: 'MyFooter',
  props: {
    completedCount: {
      type: Number,
      required: true
    },
    totalCount: {
      type: Number,
      required: true
    },
    isAllCompleted: {
      type: Boolean,
      required: true
    }
  }
};
</script>

<style scoped>
.footer {
  width: 500px;
  display: flex;
  align-items: center;
  padding: 15px 10px;
  background: #fff;
  border-radius: 6px;
  justify-content: space-between; /* 让左侧区域和右侧按钮两端对齐 */
}

.footer-left {
  display: flex; /* 让复选框和文本在左侧区域内水平排列 */
  align-items: center;
}

.footer-left input[type="checkbox"] {
  margin-right: 10px; /* 复选框和文本之间的间距 */
}

.clear-btn {
  background: #e57373;
  color: #fff;
  border: none;
  border-radius: 4px;
  padding: 6px 16px;
  cursor: pointer;
  font-size: 14px;
}
.clear-btn:hover {
  background: #d32f2f;
}
</style>

