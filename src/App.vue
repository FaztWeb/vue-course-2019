<template>
  <div id="app">
    <h1 class="app-title">
      Vue App
      <button @click="getTasks">
        <i class="fas fa-sync"></i>
      </button>
    </h1>
    <TaskForm class="task-form" @new-task="onNewTask"/>
    <Tasks class="tasks" :tasks="tasks" v-on:task-deleted="onTaskDelete"/>
  </div>
</template>

<script>
import Tasks from "./components/Tasks";
import TaskForm from "./components/TaskForm";
import { tasks } from "./tasks";

import axios from 'axios'

export default {
  data() {
    return {
      tasks
    };
  },
  components: {
    Tasks,
    TaskForm
  },
  methods: {
    onTaskDelete(id) {
      this.tasks = this.tasks.filter(task => task.id !== id);
    },
    onNewTask({ title, description }) {
      this.tasks = [
        ...this.tasks,
        {
          title,
          description,
          id: this.tasks.length,
          done: false
        }
      ];
    },
    async getTasks() {
      const response = await axios.get('https://jsonplaceholder.typicode.com/todos?_limit=5')
      const data = response.data.map(todo => ({
        title: todo.title,
        id: todo.id,
        done: todo.completed
      }));
      this.tasks = data;
    }
  }
};
</script>

<style>
.app-title {
  text-align: center;
  color: white;
  font-size: 2.3rem;
}
#app {
  margin: 0;
  height: 100%;
  padding: 5px;
}
.tasks,
.task-form {
  width: 40%;
  margin: auto;
}
.task-form {
  padding: 10px;
  border: 1px solid #fff;
  margin-bottom: 4px;
  text-align: center;
}
</style>

