<template>
    <div class="card mb-1 text-left">
        <ul class="list-group">
            <li class="list-group-item" v-for="(task,index) in tasks" :key="index">
                <div :class="task.Completed ? 'Completed' : ' '">{{ task.body }}</div>
                <div class="icons">
                    <i @click="completedTask(task)" class="fas fa-check-circle A"></i>
                    <i @click="deleteTask(index)" class="fas fa-trash-alt B ml-3"></i>
                </div>
            </li>
        </ul>
    </div>
</template>

<script>
export default {
    props: ['tasks'],
    methods: {
        completedTask: function(task) {
            this.$emit("completed-event-task",task);
        },
        deleteTask: function(index) {
            this.$emit("delete-event-task",index);        }
    }
};
</script>

<style scoped>
.Completed{
    color:green;
    text-decoration:line-through;
}
.A:hover{
    color:rgb(97, 204, 97);
}
.B:hover{
    color:red;
}
.list-group-item{
    display:flex;
    justify-content:space-between;
}
</style>