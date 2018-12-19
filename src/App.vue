
<template>
  <div id="app">
         <navbar @navbar:change="escucharnavbar"></navbar>
         <login2 @login2:change="escucharlogin2" v-if="mostrar"></login2>
         <mainview v-if="mostrarmain"></mainview>
<!--     <login2 @login2:change="escucharlogin2" v-if="mostrar"/>
         <mainview v-else/>
         <mainview/>
-->     
      <el-footer>
         <footbar/> 
      </el-footer>
  </div>
</template>


<script>


import navbar from './components/navbar.vue'
import footbar from './components/footbar.vue'
import login2 from './components/login2.vue'
import mainview from './components/mainview.vue'
import table1 from './components/table1.vue'
import table2 from './components/table2.vue'
import { EventBus } from "./main.js"

export default {
  name: 'app',
    created () {

    EventBus.$on('login2:change', () => {
      console.log('Mensaje del login2 en app.vue')
      this.mostrar = false, this.mostrarmain = true
    })
    EventBus.$on('navbar:change', () => {
      console.log('Mensaje del navbar en app.vue')
      this.mostrar = true, this.mostrarmain = false
    })
  },

  components: {
    navbar,
    footbar,
    login2,
    mainview,
    table1,
    table2
  },


 data: function(){
    return {
      mostrar: true,
      mostrarmain: false
    };
  },
  methods: {
    escucharlogin2() {
      console.log('Mensaje recibido de login2')
      this.mostrar = false
      this.mostrarmain = true
    },
    escucharnavbar() {
      console.log('Mensaje recibido de navbar')
      this.mostrar = true
      this.mostrarmain = false
    },
  }
}
</script>

<style>
#app {
  font-family: 'Avenir', Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin:0%;
  margin-bottom: 0; 
  }
</style>
