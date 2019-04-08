<template>
  <div class="tasks">
    <h1>Tasks</h1>
    <!-- Tasks -->
    <div v-for="task in tasks" :key="task.id">
      <Task :task="task" v-on:task-deleted="$emit('task-deleted', task.id)"/>
    </div>
  </div>
</template>

<script>
import Task from "./Task";
export default {
  name: "Tasks",
  components: {
    Task
  },
  props: {
    tasks: Array
  }
};
</script>

<style scoped>
h1 {
  text-align: center;
  color: #d2dae2;
}
.tasks {
  border: 1px solid #fff;
  padding: 5px 10px;
  background: #222f3e;
}
</style>
