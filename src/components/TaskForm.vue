<template>
    <form action="" @submit="addTask">
        <input type="text" v-model="title" placeholder="Title">
        <input type="text" v-model="description" placeholder="Description">
        <button class="btn" type="submit">
            Save
        </button>
    </form>
</template>

<script>
export default {
    name: 'TaskForm',
    data() {
        return {
            title: '',
            description: ''
        }
    },
    methods: {
        addTask(e) {
            e.preventDefault();
            const newTask = {
                title: this.title,
                description: this.description
            };
            this.$emit('new-task', newTask);
        }
    }
}
</script>

<style scoped>
form input[type="text"], form button {
    text-align: center;
    display: block;
    width: 70%;
    margin: 10px auto;    
    padding: 7px;
}
</style>

