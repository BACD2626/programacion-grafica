<template>
  <div class="login2" >
      <h1>Login</h1>
  <el-form :model="ruleForm2" status-icon :rules="rules2" ref="ruleForm2" label-width="120px" class="demo-ruleForm">
   
    <el-form-item label="User" prop="user">
      <el-input type="user" v-model="ruleForm2.user" autocomplete="off"></el-input>
    </el-form-item>
   
    <el-form-item label="Password" prop="pass">
      <el-input type="password" v-model="ruleForm2.pass" autocomplete="off"></el-input>
    </el-form-item>
    
    <el-form-item>
      <el-button type="success" plain @click="submitForm('ruleForm2')" >Submit</el-button>
      <el-button type="primary" plain @click="resetForm('ruleForm2')">Reset</el-button>
    </el-form-item>
    <br>
  </el-form>
  </div>
</template>

<script>
import { EventBus } from "../main.js";
export default {
name: 'login2',
    components: {
    
  },
   data: function() {

      var validateUser = (rule, value, callback) => {
        if (value === '') {
          callback(new Error('Please input the user'));
        } else {
          callback();
        }
      };

      var validatePass = (rule, value, callback) => {
        if (value === '') {
          callback(new Error('Please input the password'));
        } else {
          callback();
        }
      };

      return { 
        User: "a",
        Pass: "a",
       
        ruleForm2: {
          user: '',
          pass: '',
        },
        rules2: {
          user: [
            { validator: validateUser, trigger: 'blur' }
          ],
          pass: [
            { validator: validatePass, trigger: 'blur' }
          ]
          }
         }
        }, //Aqui termina la funcion data
        methods: {
        submitForm(formName) {  //validacion de usuario
        this.$refs[formName].validate((valid) => {
         if (valid && this.ruleForm2.user == this.User && this.ruleForm2.pass == this.Pass) {
           //alert('Welcome back!');
           this.emitirEventologin2();
           console.log('submit!!');
         } else {
           //alert('no submit! ivalid user or password');
           console.log('error submit!!');
           return false;
         }});
         },
        resetForm(formName) {
           this.$refs[formName].resetFields();
         },
        emitirEventologin2 () {
          EventBus.$emit('login2:change')
          }
       }
  }
</script>  

<style>

      .login2 {
      margin-right: 5%;
      margin-left: 0%;
      height: 2000px;
      text-align: center;
    }


</style>
