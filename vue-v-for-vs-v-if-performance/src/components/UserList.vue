<template>
  <div id="app">
    <h2>错误示例：v-if 和 v-for 一起使用</h2>
    <ul>
      <li v-for="(user, index) in users" :key="index">
        <span v-if="user.isActive">{{ user.name }}</span>
      </li>
    </ul>

    <h2>正确示例：使用计算属性优化</h2>
    <ul>
      <li v-for="(user, index) in activeUsers" :key="index">
        {{ user.name }}
      </li>
    </ul>
  </div>
</template>

<script>
export default {
  data() {
    return {
      users: [
        { name: 'Alice', isActive: true },
        { name: 'Bob', isActive: false },
        { name: 'Charlie', isActive: true },
      ]
    };
  },
  computed: {
    // 计算属性：只返回 isActive 为 true 的用户
    activeUsers() {
      return this.users.filter(user => user.isActive);
    }
  }
};
</script>

<style scoped>
h2 {
  color: #42b983;
  margin-bottom: 10px;
}
</style>