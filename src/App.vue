<template>
  <div class="container">
    <Header @toggle-add-task="toggleAddTask" title="Task Tracker" :showAddTask="showAddTask"/>
    <div v-show="showAddTask">
      <AddTask @add-task="addNewTask"/>
    </div>
    <Tasks 
      @delete-task="deleteTask" 
      @toggle-reminder="toggleReminder"
      :tasks="tasksData"
    />
  </div>
</template>

<script>
import Header from './components/Header.vue';
import Tasks from './components/Tasks.vue';
import AddTask from './components/AddTask.vue';

export default {
  name: 'App',
  components: {
    Header, Tasks, AddTask
  },
  data() {
    return {
      tasksData: [],
      showAddTask: false
    }
  },
  methods: {
    deleteTask(id) {
      if(confirm('Are you sure ?')) {
        this.tasksData = this.tasksData.filter((task) => task.id != id)
      }
    },
    toggleReminder(id) {
      this.tasksData = this.tasksData.map((task) => {
        if(task.id == id) {
          return {...task, reminder: !task.reminder};
        }
        return task;
      })
    },
    addNewTask(data) {
      this.tasksData.push(data);
    },
    toggleAddTask() {
      this.showAddTask = !this.showAddTask;
    }
  },
  created() {
    this.tasksData = [
      {
        id: 1,
        text: 'Doctors appointment 1',
        day: 'March 1st at 2:30pm',
        reminder: true
      },
      {
        id: 2,
        text: 'Doctors appointment 2',
        day: 'March 1st at 2:30pm',
        reminder: true
      },
      {
        id: 3,
        text: 'Doctors appointment 3',
        day: 'March 1st at 2:30pm',
        reminder: false
      },
      {
        id: 4,
        text: 'Doctors appointment 4',
        day: 'March 1st at 2:30pm',
        reminder: true
      }
    ]
  }
}
</script>

<style>
  @import url('https://fonts.googleapis.com/css2?family=Poppins:wght@300;400&display=swap');
  * {
    box-sizing: border-box;
    margin: 0;
    padding: 0;
  }
  body {
    font-family: 'Poppins', sans-serif;
  }
  .container {
    max-width: 500px;
    margin: 30px auto;
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
  .btn:focus {
    outline: none;
  }
  .btn:active {
    transform: scale(0.98);
  }
  .btn-block {
    display: block;
    width: 100%;
  }
</style>
