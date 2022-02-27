<template>
<header class="header">
    <h1>{{title}}</h1>
    <Button @btn-click="$emit('btn-click')" :text="showAddTask ?'Close' : 'Add' " :color="showAddTask? 'red' : 'rgb(5, 145, 226)'"/>
    <!-- <Button text="Delete" color="red"/> -->
</header>
    
</template>
<script>

import Button from "./Button"
export default {
    name:"Header",
    components:{
    Button
    },
    props:{
        title:{
           type:String,
            default:"Tasks Vue",
        },
          showAddTask:Boolean,
    }

}

</script>

<style scoped>
.header{
     display: flex;
  justify-content: space-between;
  align-items: center;
  margin-bottom: 20px;

}
</style>