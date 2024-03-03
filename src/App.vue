<template>
  <div class="container">
    <Header @toggle-show-add-task="toggleShowAddTask" title="Task Tracker"></Header>
    <AddTask v-show="this.showAddTask" @add-new-task="addNewTask" :tasks="tasks"></AddTask>
    <Task @toggle-reminder="toggleReminder" @delete-task="deleteTask" :tasks="tasks"></Task>
  </div>
</template>

<script>

import Header from './components/Header.vue'
import Task from './components/Tasks.vue';
import AddTask  from './components/AddTask.vue'

export default {
  name: 'App',
  components: {
    Header,
    Task,
    AddTask
  },
  data(){
    return {
      tasks: [],
      showAddTask: false,
    }
  },
  methods:{
    deleteTask(taskId){
      if(confirm('Are you sure! you want to delete this task ?')){
        this.tasks = this.tasks.filter(task=> task.id !== taskId)
      }
    },
    toggleReminder(taskId){
        this.tasks = this.tasks.map(task=>
          task.id === taskId ? {...task, reminder: !(task.reminder)} : task
        )
    },
    addNewTask(newTask){
      this.tasks = [...this.tasks, newTask]
    },
    toggleShowAddTask(){
      this.showAddTask = !(this.showAddTask)
    },
    async fetchTasks (){
      const response = await fetch('http://localhost:3001/tasks')
      const data = await response.json()
      return data
    }
  },
  async created(){
    this.tasks = await this.fetchTasks()
  }
}
</script>

<style>
  #app {
    font-family: Avenir, Helvetica, Arial, sans-serif;
    -webkit-font-smoothing: antialiased;
    -moz-osx-font-smoothing: grayscale;
    text-align: center;
    color: #2c3e50;
    margin-top: 60px;
  }
  .container{
    padding: 20px;
    min-height: 300px;
    border: 1px solid #2c3e50;
    border-radius: 10px;
  }
</style>
