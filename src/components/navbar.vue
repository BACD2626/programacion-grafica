<template>
  <div class="navbar">
    <el-menu class="nav" 
    mode="horizontal" 
    active-text-color="#ffd04b"
    background-color="#545c64"
    text-color="#fff">
    <el-menu-item index="1">One-Click One-Money</el-menu-item>
    <!--
    <el-menu-item index="2" v-show="option1" @click="opt1">FORMULARIO</el-menu-item>
    <el-menu-item index="3" v-show="option2" @click="opt2">DASHBOARD</el-menu-item>
    -->
    <el-menu-item index="4" v-show="logout" @click="apagar" type="text" plain  style="float:right" enabled>LOGOUT</el-menu-item>
    </el-menu>
</div>
</template>

<script>
import { EventBus } from "../main.js";

export default {
  name: 'navbar',

    created () {
    EventBus.$on('login2:change', () => {
      console.log('Mensaje del login 2 recibido en navbar')
      this.logout = true
    })
  },
      data: function() {
      return { 
      logout: false
      }
    },
    
    methods: {
      emitirEventonavbar () {
        EventBus.$emit('navbar:change')
          },
      escucharlogin2() {
        console.log('Mensaje recibido de login2 en navbar')
         
      },
      apagar: function() {

        this.emitirEventonavbar();
        //alert('Session closed!');
        this.logout = false;
    }
    },
}
</script>

<style>
    .el-menu,.navbar{
      background-color: #545c64;
      color:#fff;
      text-align:center;

      line-height: 30px;
      margin: 0;
      padding: 0;
      overflow: hidden;
      margin-right: 0%;
      margin-left: 0%;
    }
  </style>
