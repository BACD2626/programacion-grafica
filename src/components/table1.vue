<template>
  <div class="table1">


        <!--Inicia formulario form-->
          <div class="formulario">
              <br>
              <el-radio-group v-model="tabPosition" style="margin-bottom: 30px;">
                <el-radio-button label="customer">Customer</el-radio-button>
                <el-radio-button label="provider">Provider</el-radio-button>
              </el-radio-group>
              <div slot="header" class="clearfix">
                <span style="color: #409EFF"><h1 >New register</h1></span>
              </div>
              <el-form :model="ruleForm3" :rules="rules3" v-if="validar" ref="ruleForm3" label-width="120px" class="demo-ruleForm">
                <el-row :gutter="24">
                 <el-col :span="6">
                  <el-form-item label="Name" prop="name">
                    <el-input v-model="ruleForm3.name"></el-input>
                  </el-form-item>
                 </el-col>
                 
                 <el-col :span="6">
                   <el-form-item label="Date" prop="date">
                    <el-date-picker
                      v-model="ruleForm3.date"
                      type="date"
                      placeholder="Pick a day"
                      format="dd-MM-yyyy"
                      value-format="dd-MM-yyyy">
                    </el-date-picker>
                    </el-form-item>
                  </el-col>
                 <!--
                 <el-col :span="6">
                  <el-form-item label="Lastname" prop="last">
                    <el-input v-model="ruleForm3.last"></el-input>
                  </el-form-item>
                 </el-col>
                 <el-col :span="6">
                  <el-form-item label="Select City" prop="city">
                    <el-select v-model="ruleForm3.city" placeholder="City">
                      <el-option label="Panamá" value="panama"></el-option>
                      <el-option label="Other" value="other"></el-option>
                    </el-select>
                  </el-form-item>
                  </el-col>
                  <el-col :span="6">
                  <el-form-item label="Select Status" prop="status">
                    <el-select v-model="ruleForm3.status" placeholder="Status">
                      <el-option label="Active" value="Active"></el-option>
                      <el-option label="Inactive" value="Inactive"></el-option>
                    </el-select>
                  </el-form-item>
                  </el-col>
                  -->
                  </el-row>
                   

                  <el-row :gutter="24">
                  <el-col :span="12">
                  <el-form-item label="Gender" prop="gender">
                    <el-radio-group v-model="ruleForm3.gender">
                      <el-radio label="Male"></el-radio>
                      <el-radio label="Female"></el-radio>
                      <el-radio label="Other"></el-radio>
                    </el-radio-group>
                  </el-form-item>
                  </el-col>
                  <!--
                  <el-col :span="12">
                  <el-form-item label="Civil state" prop="civils">
                    <el-radio-group v-model="ruleForm3.civils">
                      <el-radio label="Single"></el-radio>
                      <el-radio label="Married"></el-radio>
                      <el-radio label="Other"></el-radio>
                    </el-radio-group>
                  </el-form-item>
                  </el-col>
                  -->
                  </el-row>
                  <!--
                  <el-form-item label="Delivery Address" prop="address">
                    <el-input type="textarea" v-model="ruleForm3.address"></el-input>
                  </el-form-item>
                  -->
                  <el-form-item>
                    <el-button type="primary" @click="submitForm3('ruleForm3')">Create</el-button>
                    <el-button @click="resetForm('ruleForm3')">Reset</el-button>
                  </el-form-item>
                </el-form>
          </div>
          <!--Termina formulario form-->


      <el-tooltip content="Click on any of the cells or on the edit button to edit content">
       <i class="el-icon-info"></i>
      </el-tooltip>
       <el-table
      :data="gridData"
      style="width: 100%">

       <el-table-column
        label="Operations"
        min-width="180">
        <template slot-scope="{row, index}">
         <el-button icon="el-icon-edit"
          @click="setEditMode(row, index)">
        </el-button>
         <el-button type="success" icon="el-icon-check"
          @click="saveRow(row, index)">
        </el-button>
        <el-button
          @click.native.prevent="deleteRow(scope.$index, gridData)"
          type="text"
          size="small">
          Eliminar
        </el-button>
        </template>
      </el-table-column>


      <el-table-column
        prop="name"
        label="Name"
        min-width="180">
        <editable-cell :show-input="row.editMode" slot-scope="{row}" v-model="row.name">
          <span slot="content">{{row.name}}</span>
        </editable-cell>
      </el-table-column>

      <el-table-column
        prop="gender"
        min-wwidth="150"
        label="Gender">

         <editable-cell 
         :show-input="row.editMode"
         slot-scope="{row}" 
         editable-component="el-select"
         close-event="change"
         v-model="row.gender">
         
          <el-tag size="medium" 
                  :type="row.gender === 'M' ? 'primary' : 'danger'" 
                  slot="content">
                  {{row.gender === 'M' ? 'Male': 'Female'}}
          </el-tag>

          <template slot="edit-component-slot">
            <el-option value="M" label="Male"></el-option>
            <el-option value="F" label="Female"></el-option>
          </template>
        </editable-cell>
        
      </el-table-column>


      <el-table-column
        prop="date"
        label="Birth Date"
        min-width="250">
         <editable-cell 
         :show-input="row.editMode"
         slot-scope="{row}" 
         editable-component="el-date-picker"
         format="dd-MM-yyyy"
         value-format="dd-MM-yyyy"
         v-model="row.date">
          <span slot="content">{{row.date}}</span>
        </editable-cell>
      </el-table-column>
    </el-table>
  </div>
</template>

<script>
import EditableCell from "./EditableCell.vue";

export default {
name: 'table1',
  components: {
    EditableCell
  },
  data() {
    
    return {
      editModeEnabled: false,
      tabPosition: 'customer',
        ruleForm3: {
        name: "",
      //last: "",
      //city: "",
      //status: "",
      //civils: "",
        gender: "",
        date: "",
      //address: "",
        },
      gridData: [],
        rules3: {
        name: [
          { required: true, message: 'Please input name', trigger: 'blur' },
          { min: 3, max: 15, message: 'Length should be 3 to 15', trigger: 'blur' }
        ],
      //last: [
      //  { required: true, message: 'Please input lastname', trigger: 'blur' },
      //  { min: 3, max: 15, message: 'Length should be 3 to 15', trigger: 'blur' }
      //],
      //city: [
      //  { required: true, message: 'Please select a city', trigger: 'change' }
      //],
      //status: [
      //  { required: true, message: 'Please select a status', trigger: 'change' }
      //],
      //civils: [
      //  { required: true, message: 'Please select a Civil status', trigger: 'change' }
      //],
        gender: [
          { required: true, message: 'Please select a gender', trigger: 'change' }
        ],
        
        date: [
         { required: false, message: 'Please select a date', trigger: 'blur' }
        ],
        
      //address: [
      //  { required: true, message: 'Please input a address', trigger: 'blur' }
      //] 
        },
    };
  },
  methods: {
    setEditMode(row, index) {
      row.editMode = true;
    },
    saveRow(row, index) {
      row.editMode = false;
    },
    deleteRow(row, index) {
    rows.splice(index, 1);
    },
     addItem: function () { //agregar campos insertados
      this.gridData.push({
    name:      this.ruleForm3.name,
    //last:      this.ruleForm3.last,
    //city:      this.ruleForm3.city,
    //status:    this.ruleForm3.status,
    //civils:    this.ruleForm3.civils,
    gender:    this.ruleForm3.gender,
    date:      this.ruleForm3.date
    //address:   this.ruleForm3.address
    })
    this.resetForm()
    },
    resetForm(formName) {
      this.$refs[formName].resetFields();
    },
    deleteRow(index, rows) {
    rows.splice(index, 1);
    },
    submitForm3: function(formName) {
    this.$refs[formName].validate((valid) => {
    console.log('Submit 3 ', formName, this.ruleForm3)
    if (valid) {
      console.log(this.ruleForm3.date);
      this.addItem()
      alert('submit!');
    } else {
      console.log('error submit!!');
      return false;
    }
    });     
    },

  },
  mounted() {
    this.gridData = this.gridData.map(row => {
      return {
        ...row,
        editMode: false
      };
    });
  },
  computed: {
  validar: function (){
    return this.tabPosition != 'provider'
  }
},
};
</script>
