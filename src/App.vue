<template>
   
  <div class="container">
 <HeaderVue @toggle-add-task ="toggleAddTask" title="Task Tracker"/>
 <div v-if="showAddTask">
 <AddTask @add-task="AddTask"/>
</div>
 <TasksVue @toggle-reminder="toggleReminder" @delete-task="deleteTask" :tasks="tasks"/>


</div>
  
</template>

<script>
import HeaderVue from './components/HeaderVue.vue';
import TasksVue from './components/TasksVue.vue';
import AddTask from './components/AddTask.vue'


export default {
  name: 'App',
  components: {
    HeaderVue,
    TasksVue,
    AddTask,
   },
   data(){
    return{
      tasks: [],
      showAddTask: false,
   }
   },
   methods: {
    toggleAddTask(){

      this.showAddTask = !this.showAddTask
    },

    AddTask(task){
      //... (spread accros) the current task and then add a new one to it
      this.tasks = [...this.tasks, task]

    }, 

    deleteTask(id){
      if(confirm('Are you sure?')){
      this.tasks = this.tasks.filter((task) => task.id !== id )
    }
  },

  toggleReminder(id){
    //change the sreminder state, maap renders an update arra, the we compare the task id to the intake id , then the initial task is changed to its oppossit value
    this.tasks = this.tasks.map((task) => task.id === id ? {...task, reminder: !task.reminder} :task)

  }


   },
   created(){
    this.tasks =[
    {id:1,
      text: 'Doctor Appointment',
      day: 'March 1st at 2:30pm',
      reminder: true,},

      {id: 2,
      text:'Meet me at School',
      day:'April 2nd at 9:00 am',
      reminder: false},
      
      {
        id: 3,
      text:'Foot Shopping',
      day:'April 2nd at 11:00 am',
      reminder: false,
        
      },
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
