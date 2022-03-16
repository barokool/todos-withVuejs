<template>
    <div>

    <form >
        <input type="text">
        <button>Sub mit</button>
    </form>
    <button @click="toggleForm">Close form</button>
    </div>
</template>

<script>
export default {
    name : "NewModal",
    data () { 
        return { 

        }
    },
    methods : { 
        toggleForm : function () { 
            this.$emit("close-form")
        }
    }
}
</script>

<style scoped>


</style>