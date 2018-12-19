<template>
    <div class="mainview">
       <!---->
  
       <br><br>
        <el-radio-group v-model="tabPosition" style="margin-bottom: 30px;">
          <el-radio-button label="customer">Customer</el-radio-button>
          <el-radio-button label="proyectos">proyectos</el-radio-button>
          

        </el-radio-group>
       <!---->
      <customers v-show="validar"></customers>
      <proyectos v-show="validar2"></proyectos> 
   
    </div>
</template>


<script>
import EditableCell from "./EditableCell.vue";
import customers    from "./customers.vue";
import proyectos    from "./proyectos.vue";
export default {
name: 'mainview',
  components: {
    EditableCell,
    customers,
    proyectos
  },
      data: function() {
        
      return { 
         tabPosition: 'customer',

        }
      
        }, //Aqui termina la funcion data
      computed: {  //Esta funcion validará si se muestran o no algunos componentes
        validar: function (){
          return this.tabPosition != 'proyectos'
        },
        validar2: function (){
          return this.tabPosition != 'customer'
        },
      },
  
      methods: {

        },

}
</script>

<style>
    .mainview {
      background-color: #E9EEF3;
      color: #333;
   
      bottom: 0;
      width: 100%;
      height: 2000px;
    }
</style>

