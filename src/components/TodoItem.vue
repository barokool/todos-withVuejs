<template>
  <p v-bind:class="[TodoItem.completed ? 'is-completed' : '']">
      <input type="checkbox" @change="markCompleted" >
      {{TodoItem.title}}
      <button @click="deleteTodo">Delete</button>
  </p>
</template>

<script>
export default {
    name : "TodoItem",
    props : ['TodoItem'],
    setup(props,context){
        const markCompleted = () => { 
            context.emit("item-completed", props.TodoItem.id)
        }

        const deleteTodo = () => { 
            context.emit("item-deleted", props.TodoItem.id)
            console.log(props.TodoItem.id)
        }
        return {
            markCompleted,
            deleteTodo
        }
    }
    
}
</script>

<style>
.is-completed { 
    text-decoration: line-through;
}
</style>