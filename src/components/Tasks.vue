<template>
    <div>
        <div class="card mb-1 text-left">
            <ul class="list-group">
                <li class="list-group-item" v-for="(task,index) in tasks" :key="index">
                    <div :class="task.completed ? 'completed' : ''">
                        {{ task.body }}
                    </div>
                    <div class="icons">
                        <i @click.prevent="completeTask(task)" class="fas fa-check-circle"></i>
                        <i @click.prevent="deleteTask(index)" class="fas fa-trash-alt ml-3"></i>
                    </div>
                </li>
            </ul>
        </div>
    </div>
</template>

<script>
export default {
    props: {
        tasks: null
    },
    methods: {
        completeTask(task){
            this.$emit("completeTaskEvent", task);
         },
        deleteTask(index){
            this.$emit('deleteTaskEvent', index);
        }
    }
};
</script>

<style scoped>
.completed {
    color: green;
    text-decoration: line-through;
}

.list-group-item {
    display: flex;
    justify-content: space-between;
}
</style>