<template>
<li>
  <div>{{ task.name }}</div>
  <small>{{ task.dueDate }} @ {{ task.dueTime }}</small>
  <button @click="removeItem(task.id)">X</button>
</li>
</template>

<script>
export default {
  name: 'Task',
  props: {
    task: Object,
    removeItem: Function,
  },
};
</script>

<style scoped>

</style>
