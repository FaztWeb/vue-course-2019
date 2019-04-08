<template>
  <div class="task" :class="{'is-done': task.done}">
    <h3>{{task.title}}</h3>
    <p>{{task.description}}</p>
    <p style="text-align: center;">
      <button class="btn-completed" @click="toggleDone">
        Completed
      </button>
      <button class="btn-deleted" @click="deleteTask">
        Delete
      </button>
    </p>
  </div>
</template>

<script>
export default {
  name: "Task",
  props: {
    task: {
      title: String,
      description: String,
      id: Number,
      done: Boolean
    }
  },
  methods: {
    toggleDone() {
      this.task.done = !this.task.done;
    },
    deleteTask() {
      this.$emit('task-deleted', this.task.id);
    }
  }
};
</script>

<style>
.task {
  background: #333;
  padding: 5px;
  border: 1px solid black;
  margin: 4px 0px;
}
.task h1,
.task h3,
.task p {
  margin: 1px 5px;
}
.is-done {
  text-decoration: line-through;
  opacity: 0.5;
}

.btn-completed {
  background: green;
  border: none;
  padding: 10px;
  color: #fff;
  margin-right: 10px;
}

.btn-deleted {
  background: red;
  border: none;
  padding: 10px;
  color: #fff;
}
</style>

