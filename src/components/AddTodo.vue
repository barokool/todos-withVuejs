<template>
  <form @submit="addItem">
      <input type="text" v-model="title">
      <input type="submit" value="Add todo here">
  </form>

</template>

<script>
import {ref} from 'vue'
export default {
    name : 'AddTodo',
    setup(props,context) { 
        const title = ref('')

        const addItem = e => { 
            e.preventDefault()
            
            const newItem = { 
                id : Math.random(),
                title : title.value,
                completed : false
            }
            context.emit("add-item", newItem)
            console.log(newItem)

        title.value=''
            
        }


        return {
            title,
            addItem
        }

    }
}
</script>

<style>

</style>