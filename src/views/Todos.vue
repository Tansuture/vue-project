<template>
  <div> 
    <router-link to ="/">Home</router-link>
    <AddTodo v-on:add-todo = "addTodo"/>
    <select v-model="filter">
        <option value="all">All</option>
        <option value="completed">completed</option>
        <option value="not-completed">not-completed</option>
    </select>
    <Todo
    v-if="filteredTodos.length"
     v-bind:todos="filteredTodos"
    @remove-todo = "removeItem"
    />
   <p v-else>No Todos</p>
  </div>
</template>

<script>
import Todo from '@/components/Todo'
import AddTodo from '@/components/AddTodo'

export default{

  components:{
    Todo,
    AddTodo
  },
   data() {
    return{
      todos:[
        {id:1,title:'buy bread',completed:false},
        {id:2,title:'vacuum house',completed:false},
        {id:3,title:'wash dishes',completed:false}
      ],
      filter:'all'
    }
  
  } ,
  computed:{
      filteredTodos(){
          var filter
          if(this.filter === "all")
          {filter=this.todos} 
          if(this.filter === "completed") 
        {filter = this.todos.filter(t => t.completed)}
         if(this.filter === "not-completed") 
         { filter = this.todos.filter(t => !t.completed)} 
         return filter
}

  },
  methods:{
    removeItem(id) {
      this.todos = this.todos.filter(t=>t.id !== id)
    },
    addTodo(todo){
      this.todos.push(todo)
    }
  }
}
</script>