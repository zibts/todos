<template>
  <div id="app">
    <Header @toggle-add-task="toggleAddTask" title="Hi" :showAddTask="showAddTask" />
    <div v-show="showAddTask">
    <AddTask @add-task="addTask"/>  
    </div>
    <Tasks @toggle-reminder="toggleReminder" @delete-task="deleteTask" :tasks="tasks"/>

  </div>
</template>

<script>
import Header from "./components/Header.vue";
import Tasks from "./components/Tasks.vue";
import AddTask from "./components/AddTask.vue";

export default {
  name: "App",
  components: {
    Header,
    Tasks,
    AddTask,
  },
  data() {
    return {
      tasks: [],
      showAddTask : false,
    };
  },
  methods: {
    deleteTask(id) {
      if(confirm('Are you sure')){ 
      this.tasks = this.tasks.filter((task)=> task.id!== id)
      }
    },
    toggleReminder(id){
      this.tasks = this.tasks.map((task)=>task.id==id?{...task,reminder:!task.reminder}:task)
    },
    addTask(task) {
      this.tasks = [...this.tasks,task]
    },
    toggleAddTask() { 
      this.showAddTask = !this.showAddTask
    }
  },
  created() {
    this.tasks = [
      {
        id: 1,
        text: "Doctors Appointment",
        day: "March First",
        reminder: true,
      },
      {
        id: 2,
        text: "Math Exam",
        day: "March Second",
        reminder: false,
      },
      {
        id: 3,
        text: "Doctors Appointment",
        day: "March Third",
        reminder: true,
      }
    ];
  },
};
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
</style>
