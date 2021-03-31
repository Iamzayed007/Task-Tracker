<template>
<div class="container">
  <Header title=" Task Tracer" />
  <AddTask
  @add-task="addTask"
  />
  <Tasks 
  
  @toggle-reminder="toggleReminder"
  @delete-task="deleteTask" :tasks="tasks"
  />

</div>
</template>

<script>
// import HelloWorld from './components/HelloWorld.vue'
import Header from './components/Header.vue'
import Tasks from './components/Tasks'
import AddTask from './components/AddTask'
export default {
  name: 'App',
  components: {
    Header,
    Tasks,
    AddTask
    
  },
    methods:{
      addTask(task)
      {
        this.tasks=[...tasks,task]
      },
    deleteTask(id){
      if(confirm('Are you sure?')){

        this.tasks=this.tasks.filter((task)=>task.id !==id)
      }
    },

    toggleReminder(id)
    {
    
      this.tasks= this.tasks.map((task)=> task.id===id ? {...task,reminder:!task.reminder} :task)
    },

  },
  data(){
return{
  tasks:[]
}
  },
  created(){
    this.tasks=[
      {
        id: 1,
        text: 'Doctors Appointment',
        day:'March 1st at 2:30 pm',
        reminder: true,
      },
      {
        id: 2,
        text: 'Meeting Appointment',
        day:'March 3rd at 2:30 pm',
        reminder: true,
      },
      {
        id: 3,
        text: 'Shopping',
        day:'March 4th at 2:30 pm',
        reminder: false,
      }

    ]
  } ,

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
.container {
   max-width: 500px;
  margin: 30px auto;
  overflow: auto;
  min-height: 300px;
  border: 1px solid steelblue;

  padding: 30px;
  border-radius: 5px;
}
.btn{

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
