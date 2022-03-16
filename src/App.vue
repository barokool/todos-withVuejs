<template>
<div>
  <img alt="Vue logo" src="./assets/logo.png">
  <!-- <HelloWorld msg="Welcome to Your Vue.js App"/> -->
  <HeaderVue msg="hello" numbs=1 />
  <Todos/>

  <h3>contitional rending and show up pop up</h3>
  <div :class="[isPopup ? 'Popup' : '']">
      <button v-if="!isPopup" @click="toggleForm">Open the form</button>
      <new-modal v-if="isPopup" @close-form="toggleForm"/>
  </div>

  <ask-question/>

  <div class="demo">
    <button 
          v-for="tab in tabs"
          v-bind:key="tab"
          @click="changeTab(tab)"
          :class="[currentTab===tab ? 'active' : '']"
    >
      {{tab}}
    </button>
    <component :is="currentTab"></component>
  </div>
</div>
</template>

<script>
import HeaderVue from './components/HeaderVue.vue'
// import HelloWorld from './components/HelloWorld.vue'
import Todos from './components/Todos.vue'
import NewModal from './components/NewModal.vue'
import AskQuestion from './components/AskQuestion.vue'
import Archive from './components/pagesComponent/Archive.vue'
import Home from './components/pagesComponent/Home.vue'
import Post from './components/pagesComponent/Post.vue'

export default {
  name: 'App',
  components: { HeaderVue,Todos,NewModal,AskQuestion,Archive,Home,Post },
  data () { 
    return { 
      isPopup : false,
      currentTab : 'Home',
      tabs : ['Home','Post','Archive']
    }
  },
  methods : { 
    toggleForm : function () { 
      this.isPopup = !this.isPopup
    },
    changeTab : function (tab) { 
      this.currentTab = tab
    }
  }
}
</script>

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}
.Popup { 
  background : rgba(0,0,0,0.5)
}
.active { 
  background : yellow;
}

</style>
