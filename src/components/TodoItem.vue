<template>
    <div>
        <li>
            <span v-bind:class="{done:todo.completed}">
                <input v-on:change="todo.completed=!todo.completed" 
                type="checkbox">
                {{todo.title}}
            </span>
            <button
            v-on:click="$emit('remove-todo',todo.id)"
             class="btn"
            >&times;</button>
        </li>
    </div>
</template>

<script>
export default {
    props:[
        'todo'
    ]
}
</script>

<style>
li{
    border:1px solid gainsboro;
    display: flex;
    justify-content: space-between;
    padding:10px 5px;
}
.btn{
    border-radius: 50%;
    background: red;
}
.done{
    text-decoration: line-through;
}
</style>