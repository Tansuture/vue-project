<template>
    <div>
        <ul>
       <TodoItem
         v-for="(todo,index) in todos" :key=index
        v-bind:todo="todo"
        v-on:remove-todo="removeItem"
        />
        </ul>
       
    </div>
</template>

<script>
import TodoItem from '@/components/TodoItem'

export default{
    props:['todos'],
    components :{
        TodoItem
    },
    methods:{
        removeItem(id){
           
            this.$emit('remove-todo', id)

        }
    }
 }
    
</script>

<style scoped>



</style>