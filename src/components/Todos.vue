<template>
<div>
  <TodoItem v-for="todo in todos" todo="todo" v-bind:key="todo.id" v-bind:TodoItem="todo" @item-completed="markCompleted"/>
</div>
</template>

<script>
import {ref} from 'vue'
import TodoItem from './TodoItem.vue'
export default {
    name : "Todos",
    components : {TodoItem},
    setup() { 
        const todos = ref([
            {
                id : 1,
                title : "viec 1",
                completed : false,
            },
            {
                id : 2,
                title : "viec 2",
                completed : false,
            },{
                id : 3,
                title : "viec 3",
                completed : false,
            },
        ])

        const markCompleted = id => { 
            todos.value = todos.value.map(todo => { 
                if (todo.id === id )
                    todo.completed = !todo.completed
                return todo
            })
        }
        

        return {
            todos,
            markCompleted
        }
    }
}
</script>

<style>

</style>