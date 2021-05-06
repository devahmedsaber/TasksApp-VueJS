<template>
  <div id="app">
    <h3>{{ title }}</h3>
    <Tasks :tasks="tasks" v-on:completeTaskEvent="completeTask" v-on:deleteTaskEvent="deleteTask"></Tasks>
    <input @keyup.enter="addNewTask" type="text" class="form-control mb-2" v-model="newTask">
    <button v-on:click="addNewTask" class="btn btn-success btn-block">Add New Task</button>
  </div>
</template>

<script>
import Tasks from '@/components/Tasks';
export default {
  name: 'App',
  components: {
    Tasks
  },
  data (){
    return {
      title: "Saber Tasks App",
      newTask: null,
      tasks: [
        {
          body : 'Go To Shop',
          completed: false
        },
        {
          body : 'Go To Barber',
          completed: false
        },
        {
          body : 'Go To Cinema',
          completed: false
        }
      ]
    };
  },
  methods: {
    addNewTask(){
      this.tasks.push({
        body: this.newTask,
        completed: false
      });
      this.newTask = null;
    },
    completeTask(task){
      task.completed = !task.completed;
    },
    deleteTask(index){
      console.log('Delete Task : ' + index);
      this.tasks.splice(index, 1);
    }
  }
};
</script>

<style>
#app {
  margin-top: 60px;
}

.card {
  padding: 20px;
  background: #EEE;
}
</style>
