<template>
    <button  class="btn" @click="$emit('btn-click')"   :style="{background:color}">{{text}}</button>
</template>


<script>
export default {
    name:"Button",
    props:{
        text:String,
         
        color:String,
        
     

    },
    methods:{
        handleClick(){
            this.$emit('btn-click')
        }
    }
}
</script>


<style scoped>
.btn{
display: inline-block;
  background: lightseagreen;
  color: #fff;
  border: none;
  padding: 10px 25px;
  margin: 5px;
  border-radius: 5px;
  cursor: pointer;
  text-decoration: none;
  font-size: 15px;
  font-family: inherit;
  font-weight: 600;
}
button:active{
 transform: scale(1.03);
}
button:hover{
  font-weight: 800;
}

</style>