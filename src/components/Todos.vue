<template>
<div>
        <AddTodo @add-item="addTodo"/>
        <TodoItem 
        v-for="todo in todos" 
        :key="todo.id" 
        :TodoItem="todo" 
        @item-completed="markCompleted" 
        @item-deleted="deleteTodo"/>
        
</div>
</template>

<script>
import {ref} from 'vue'
import TodoItem from './TodoItem.vue'
import AddTodo from './AddTodo.vue'
export default {
    name : "Todos",
    components : {TodoItem,AddTodo},
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
        
        const deleteTodo = id => { 
            todos.value = todos.value.filter(todo => {
               return todo.id !== id })
        }

        const addTodo = item => { 
            todos.value.push(item)

            return todos
        }

        return {
            todos,
            markCompleted,
            deleteTodo,
            addTodo
        }
    }
}
</script>

<style>

</style>