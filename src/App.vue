
<template>
  <div class="container">
    <Header @toggle-add-task="toggleAddTask" title="Task Tracker" :showAddTask="showAddTask" />
   <div v-if="showAddTask">
     <AddTask @add-task="addTask" />
   </div>
    <Tasks @toggle-reminder="toggleReminder" @delete-task="deleteTask" :tasks="tasks" />
    
  
  </div>
</template>


<script>
import Header from './components/Header.vue'
import Tasks from './components/Tasks.vue'
import AddTask from './components/AddTask.vue'
export default {
  name: 'App',
  components: {
    Header,
    Tasks,
    AddTask
    
  
    
},
  data() {
    return {
      tasks: [],
      showAddTask: false
    }
  },
  methods: {
    toggleAddTask() {
      this.showAddTask = !this.showAddTask

    },
    addTask(task) {
      this.tasks = [...this.tasks, task]
    },
    deleteTask(id) {
      if (confirm('Are you sure?')) {
        this.tasks = this.tasks.filter((task) => task.id !== id)
      }
    },
    toggleReminder(id) {
      this.tasks = this.tasks.map((task) => task.id === id ? { ... task, reminder: !task.reminder } : task
      )

    },
  },
  created() {
    this.tasks = [
      {
      id: 1,
      text: 'meeting at school',
      day: 'March 29 at 2pm',
      reminder: true,
    },
    {
      id: 2,
      text: 'starting work',
      day: 'March 2 at 7am',
      reminder: true,
    },
    {
      id: 3,
      text: 'taking a walk',
      day: 'april 29 at 9pm',
      reminder: false,
    },
    {
      id: 4,
      text: 'going for a swim',
      day: 'feb 29 at 2pm',
      reminder: false,
    }
    ]
  }
}

</script>

<style scope>
@import url('https://fonts.googleapis.com/css2?family=Rubik&display=swap');
header {
  line-height: 1.5;
}
* {
  box-sizing: border-box;
  margin: 0;
  padding: 0;
}
body {
  font-family: 'Courier New', Courier, monospace;
}
.container {
  max-width: 500px;
  margin: 30px;
  overflow: auto;
  min-height: 300px;
  border: 1px solid steelblue;
  padding: 30px;
  border-radius: 5px;
}
.btn {
  display: inline-block;
  background: #000;
  color: #fff;
  border: none;
  padding: 10px 20px;
  margin: 5px;
  border-radius: 5px;
  cursor: pointer;
  text-decoration: none;
  font-size: 15px;
  font-family: inherit;
}
</style>

















