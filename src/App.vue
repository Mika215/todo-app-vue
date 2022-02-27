<template>
<div class="container">

 
   <Header @btn-click="setShowAddTask" title="Todo List"   :showAddTask="showAddTask" />
   <div v-show="showAddTask">
  <AddTask  @add-task="addTask"/>
   </div>
 
    <div class="taskcon">
      <Tasks @delete-task="deleteTask" @handle-remi="setReminder"  :tasks="tasks"/>
    </div>
  
   

 
</div>

</template>

<script>

import Header from "./components/Header"
import Tasks from "./components/Tasks"
import AddTask from "./components/AddTask"

export default {
  name: 'App',
  components: {
   Header,
   Tasks,
   AddTask,
  },
  data(){
    return{
      tasks:[],
      showAddTask:false,
       
    }
  },

  created(){
    this.tasks=[

{
  id:1,
  text:"Master Vue",
  date:"29 Feb 2022",
  reminder:true,
  status:"pending"
},
{
  id:2,
  text:"Go to Mathilde",
  date:"28 Feb 2022",
  reminder:true,
  status:"pending"
},
{
  id:3,
  text:"Infinity Mobile",
  date:"29 Feb 2022",
  reminder:false,
  status:"pending"
}
    ]
  },
  methods:{


setShowAddTask(){
  this.showAddTask=!this.showAddTask
},

addTask(newTask){

  this.tasks=[...this.tasks,newTask]
},

    deleteTask(taskId){
     if(confirm("Are you sure\nyou want to delete this task?")){
    this.tasks=this.tasks.filter((task)=>task.id!==taskId)
     }
    },
    setReminder(taskId){

      this.tasks=this.tasks.map((task)=>task.id===taskId?
      {...task,reminder:!task.reminder}:task)

    }
  }

}
</script>

<style>
#app {


max-width: 410px;
  margin: 30px auto;
  overflow: auto;
  min-height: 300px;
  border: 1px solid steelblue;
  padding: 30px;
  border-radius: 10px;
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  
}





</style>
