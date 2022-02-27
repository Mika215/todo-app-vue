<template>
     <div @dblclick="$emit('handle-remi',task.id)" :class="[task.reminder ? 'reminder' : '','task']">
        <h3>{{task.text}} 
          <i @click="$emit('delete-task',task.id)" class="fas fa-times"></i>
        </h3>
        <p>{{task.date}}</p>

    </div>
</template>

<script>
export default{
    name:"Task",
    props:{
        task:Object,
    
    },
    methods:{
       
              
        }
    }


</script>


<style scoped>
.fas{
 color: red;
}


.task {
   
  background: #f4f4f4;
  margin: 5px;
  padding: 2px 20px;
  cursor: pointer;

}
.task h3{
  display: flex;
  align-items: center;
  justify-content: space-between;
}

.task.reminder {
  border-left: 3px solid rgb(64, 173, 236);
}

</style>
