<template>
  <div id="app">
    <h2 class="text-center text-white mb-5">{{ title }}</h2>
    <tasks :tasks="tasks" @completed-event-task="completedTask" @delete-event-task="deleteTask"></tasks>
    <input @keyup.enter="addNewTask" type="text" class="form-control mb-2" v-model="newTask">
    <button @click="addNewTask" class="btn btn-success btn-block">Add New Task</button>
  </div>
</template>

<script>
import tasks from './components/tasks.vue';

export default {
  name: 'App',
  components: {
      tasks
  },
    data: function() {
        return {
            title: 'Tasks App',
            newTask: null,
            tasks: [
                {
                    body: 'Go To School',
                    Completed: false,
                },
                {
                    body: 'Go To Bed',
                    Completed: false,
                },
                {
                    body: 'Go To Shop',
                    Completed: false,
                },
                {
                    body: 'Go To Hospital',
                    Completed: false,
                },
                {
                    body: 'Go To Club',
                    Completed: false,
                },
            ],
        }
    },
    methods: {
        addNewTask: function() {
            this.tasks.push({
                body: this.newTask,
                Completed: false,
            })
            this.newTask = null;
        },
        completedTask: function(task) {
            task.Completed = !task.Completed;
        },
        deleteTask: function(index) {
            this.tasks.splice(index , 1);
        },
    },
}
</script>

<style>
#app {
  
  margin-top: 60px;
}
.card{
    padding:20px;
    background:#eee;
    border-radius:15px;
}
</style>
