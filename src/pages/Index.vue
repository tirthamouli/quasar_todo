<template>
  <q-page padding>
    <ul>
      <task v-for="task in tasks" :key="task.id" :task="task" :removeItem="removeItem" />
    </ul>
  </q-page>
</template>

<script>
import Task from '../components/tasks/Tasks.vue';

export default {
  name: 'Index',
  data() {
    return {
      tasks: [
        {
          id: 1, name: 'Go to shop', dueDate: '2020/06/03', dueTime: '6:30',
        },
        {
          id: 2, name: 'Get bananas', dueDate: '2020/06/04', dueTime: '7:30',
        },
        {
          id: 3, name: 'Get apples', dueDate: '2020/06/05', dueTime: '8:30',
        },
      ],
    };
  },
  methods: {
    removeItem(id) {
      this.tasks = this.tasks.filter((task) => task.id !== id);
    },
  },
  components: {
    Task,
  },
};
</script>
