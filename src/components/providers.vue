<template>
    <div class="providers">
       <!---->
        <!--Inicia formulario form-->
             <span style="color: #409EFF"><h1 >New provider register</h1></span>
              <el-form :model="ruleForm3" :rules="rules3" ref="ruleForm3" label-width="120px" class="demo-ruleForm">
                <el-row :gutter="24">
                 <el-col :span="6" >
                  <el-form-item label="Name" prop="name">
                    <el-input v-model="ruleForm3.name" placeholder="Name"></el-input>
                  </el-form-item>
                 </el-col>
                 <el-col :span="6">
                   <el-form-item label="Start Date" prop="date" >
                    <el-date-picker
                      v-model="ruleForm3.date"
                      type="date"
                      placeholder="Pick a day"
                      format="dd-MM-yyyy"
                      value-format="dd-MM-yyyy">
                    </el-date-picker>
                    </el-form-item>
                  </el-col>


                 <el-col :span="6">
                  <el-form-item label="Capital" prop="capital">
                    <el-input v-model="ruleForm3.capital" placeholder="B/."></el-input>
                  </el-form-item>
                 </el-col>

                  <el-col :span="6">
                  <el-form-item label="Type" prop="type">
                    <el-select v-model="ruleForm3.type" placeholder="type">
                      <el-option label="Private" value="private"></el-option>
                      <el-option label="Public" value="public"></el-option>
                    </el-select>
                  </el-form-item>
                  </el-col>

                  </el-row>
                  <el-row :gutter="24">
                  <el-col :span="16">
                  <el-form-item label="Activity type">
                  <el-checkbox-group v-model="ruleForm3.activity">
                    <el-checkbox label="Online activities" name="online"></el-checkbox>
                    <el-checkbox label="Promotion activities" name="promotions"></el-checkbox>
                    <el-checkbox label="Offline activities" name="offline"></el-checkbox>
                    <el-checkbox label="Simple brand exposure" name="branding"></el-checkbox>
                  </el-checkbox-group>
                  </el-form-item>
                  </el-col>
                  <el-col :span="8">
                  <el-form-item label="Estimated" prop="estimated">
                   <el-select v-model="ruleForm3.estimated" placeholder="Delivery">
                      <el-option label="1 week" value="1w"></el-option>
                      <el-option label="2 weeks" value="2w"></el-option>
                      <el-option label="1 month" value="1m"></el-option>
                      <el-option label="3 months" value="3m"></el-option>
                    </el-select>
                  </el-form-item>
                  </el-col>
                  </el-row>

                  <el-form-item label="Address" prop="address">
                    <el-input type="textarea" v-model="ruleForm3.address" placeholder="Insert address"></el-input>
                  </el-form-item>

                  <el-form-item>
                    <el-button type="primary" @click="submitForm3('ruleForm3')">Create</el-button>
                    <el-button @click="resetForm('ruleForm3')">Reset</el-button>
                  </el-form-item>
                </el-form>
          
          <!--Termina formulario form-->
          <!--Dashboard-->
       
                <el-table :data="gridData" style="width: 100%" >
                  <el-table-column
                    sortable 
                    fixed
                    prop="name"
                    label="Name"
                    width="auto">
                  </el-table-column>
                <el-table-column
                  prop="date"
                  format="dd-MM-yyyy"
                  value-format="dd-MM-yyyy"
                  label="Start Date"
                   style="width: 100%;">
                </el-table-column>
                <el-table-column
                    prop="capital"
                    label="Capital"
                    width="auto">
                  </el-table-column>
                  <el-table-column
                    prop="type"
                    label="Type"
                    width="auto">
                  </el-table-column>
                  <el-table-column
                    prop="activity"
                    label="Activities"
                    width="auto">
                  </el-table-column>
                  <el-table-column
                    prop="estimated"
                    label="Estimated Delivery"
                    width="auto">
                  </el-table-column>
                  <el-table-column
                    prop="address"
                    label="Delivery Address"
                    width="auto">
                  </el-table-column>
                  <el-table-column
                    prop="operations"
                    label="Operations"
                    width="auto">
                  <template slot-scope="scope">
                  <el-button
                    @click.native.prevent="deleteRow(scope.$index, gridData)"
                    type="text"
                    size="small">
                    Eliminar
                  </el-button>
                   <el-button type="primary" @click="editData(scope.$index, gridData)">Edit</el-button>
                  </template>
                  </el-table-column>
                </el-table>
               
         
          <!--Termina dashboard-->
    </div>
</template>


<script>
import EditableCell from "./EditableCell.vue";
export default {
name: 'providers',
  components: {
    EditableCell
  },
      data: function() {
        
      return { 
         tabPosition: 'customer',
         editMode: false,
        ruleForm3: {
        name: "",
        date: "",
        capital: "",
        type: "",
        activity: [],
        estimated: "",
        address: "",
        
        },
        gridData: [],

        rules3: {
          name: [
            { required: true, message: 'Please input name', trigger: 'blur' },
            { min: 3, max: 15, message: 'Length should be 3 to 15', trigger: 'blur' }
          ],
          date: [
           { required: true, message: 'Please select a date', trigger: 'blur' }
          ],
          capital: [
            { required: true, message: 'Please input your capital', trigger: 'blur' }
          ],
          type: [
            { required: true, message: 'Please select a city', trigger: 'change' }
          ],
          activity: [
            { required: true, message: 'Please select a status', trigger: 'blur' }
          ],
          estimated: [
            { required: true, message: 'Please select a Civil status', trigger: 'change' }
          ],

          address: [
            { required: true, message: 'Please input a address', trigger: 'blur' }
          ] 
          },
        }
      
        }, //Aqui termina la funcion data
      computed: {  //Esta funcion validará si se muestran o no algunos componentes

        validar2: function (){
          return this.tabPosition != 'customer'
        },
      },
  
      methods: {
        addItem: function () { //agregar campos insertados
          this.gridData.push({
          name:         this.ruleForm3.name,
          date:         this.ruleForm3.date,
          capital:      this.ruleForm3.capital + ", ",
          type:         this.ruleForm3.type,
          activity:     this.ruleForm3.activity,
          estimated:    this.ruleForm3.estimated,
          address:      this.ruleForm3.address
        })
        },
        resetForm(ruleForm3) {
          this.$refs[ruleForm3].resetFields();
        },
        deleteRow(index, rows) {
        rows.splice(index, 1);
        alert('Register deleted!');
        console.log('Register deleted!');
        },
        editData (gridData) {
          this.beforEditCache = gridData
          this.editedTable = gridData
        },

        submitForm3: function(formName) {
        this.$refs[formName].validate((valid) => {
        console.log('Submit', formName, this.ruleForm3)
        if (valid) {
          console.log('New register saved');
          this.addItem()
          alert('New register saved!');
        } else {
          console.log('error submit!!');
          return false;
        }
        });     
        },
        filterHandler(value, row, column) {
        const property = column['property'];
        return row[property] === value;
      }
        },
          mounted() {
        this.gridData = this.gridData.map(row => {
            return {
              ...row,
              editMode: false
            };
          });
        }
}
</script>


<style>
    .providers {
      background-color: #E9EEF3;
      color: #333;
      width: 100%;
      margin-right: 5%;
    }

</style>
