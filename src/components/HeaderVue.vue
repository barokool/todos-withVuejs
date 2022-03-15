<template>
  <div>
              {{msg}} + {{numbs}}
  </div>
</template>

<script>
export default {
    name : "HeaderVue",
    props : { 
        msg:String,
        numbs : Number
    }
}
</script>

<style>

</style>