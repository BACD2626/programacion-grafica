<template>
    <div class="customers">
       <!---->
        <!--Inicia formulario form-->
              <span style="color: #409EFF"><h1 >REGISTRO DE NUEVO PROYECTO</h1></span>
              <el-form :model="ruleForm3" :rules="rules3" ref="ruleForm3" label-width="120px" class="demo-ruleForm">
                <el-row :gutter="24">

                 <el-col :span="6" >
                  <el-form-item label="Nombre" prop="name">
                    <el-input v-model="ruleForm3.name" placeholder="Name"></el-input>
                  </el-form-item>
                 </el-col>

                 <el-col :span="6" v-if="validar">
                  <el-form-item label="fecha de lanzamiento" prop="last">
                    <el-input v-model="ruleForm3.last"></el-input>
                  </el-form-item>
                 </el-col>

                 <el-col :span="6" v-if="validar">
                  <el-form-item label="ingrese categoria" prop="city">
                    <el-select v-model="ruleForm3.city" placeholder="Categoria">
                      <el-option label="Navegadores y Sistemas Operativos" value="Navegadores y Sistemas Operativos"></el-option>
                      <el-option label="Plataformas móviles" value="Plataformas móviles"></el-option>
                      <el-option label="Lenguajes de programación" value="Lenguajes de programación"></el-option>
                      <el-option label="Aplicaciones de trabajo" value="Aplicaciones de trabajo"></el-option>
                    </el-select>
                  </el-form-item>
                  </el-col>

                  <el-col :span="6" v-if="validar">
                  <el-form-item label="Select Status" prop="status">
                    <el-select v-model="ruleForm3.status" placeholder="Status">
                      <el-option label="Active" value="Active"></el-option>
                      <el-option label="Inactive" value="Inactive"></el-option>
                    </el-select>
                  </el-form-item>
                  </el-col>
                  </el-row>
                  <el-row :gutter="24">
                    <!--
                  <el-col :span="12" v-if="validar">
                  <el-form-item label="Gender" prop="sex">
                    <el-radio-group v-model="ruleForm3.sex">
                      <el-radio label="Male"></el-radio>
                      <el-radio label="Female"></el-radio>
                      <el-radio label="Other"></el-radio>
                    </el-radio-group>
                  </el-form-item>
                  </el-col>
                  
                  <el-col :span="12" v-if="validar">
                  <el-form-item label="Civil status" prop="civils">
                    <el-radio-group v-model="ruleForm3.civils">
                      <el-radio label="Single"></el-radio>
                      <el-radio label="Married"></el-radio>
                      <el-radio label="Other"></el-radio>
                    </el-radio-group>
                  </el-form-item>
                  </el-col>
                  -->
                  </el-row>

                  <el-form-item label="Descripcion del proyecto" prop="address" v-if="validar">
                    <el-input type="textarea" v-model="ruleForm3.address" placeholder="Descripcion"></el-input>
                  </el-form-item>

                  <el-form-item label="Link del proyecto o Repositorio" prop="link" v-if="validar">
                    <el-input type="textarea" v-model="ruleForm3.link" placeholder="Link/Repositorio"></el-input>
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
                    label="Nombre"
                    width="auto">
                  </el-table-column>
                  <el-table-column
                    prop="last"
                    label="Lanzamiento"
                    width="auto">
                  </el-table-column>
                  <el-table-column
                    prop="city"
                    label="categoria"
                    width="auto">
                  </el-table-column>
                  <el-table-column
                    prop="status"
                    label="Status"
                    width="auto">
                  </el-table-column>
                  <!--
                  <el-table-column
                    prop="civils"
                    label="Civil  Status"
                    width="auto">
                  </el-table-column>
                  <el-table-column
                  prop="sex"
                  label="Gender"
                  width="auto">
                </el-table-column>
                -->
                  <el-table-column
                    prop="address"
                    label="Descripcion "
                    width="auto">
                  </el-table-column>
                  <el-table-column
                    prop="link"
                    label="link "
                    width="auto">
                  </el-table-column>
                  <!--
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
                  -->
                </el-table>     
          <!--Termina dashboard-->

    </div>
</template>


<script>
import EditableCell from "./EditableCell.vue";
export default {
name: 'customers',
  components: {
    EditableCell
  },
      data: function() {
        
      return { 
         tabPosition: 'customer',
         editMode: false,
        ruleForm3: {
        name: "",
        last: "",
        city: "",
        status: "",
        civils: "",
        sex: "",
        link: "",
        address: "",
        activity: [],
        },
        gridData: [],

        rules3: {
          name: [
            { required: true, message: 'Ingrese nombre', trigger: 'blur' },
            { min: 3, max: 15, message: 'Length should be 3 to 15', trigger: 'blur' }
          ],
          last: [
            { required: true, message: 'Ingrese fecha de lanzamiento', trigger: 'blur' },
            { min: 3, max: 15, message: 'Length should be 3 to 15', trigger: 'blur' }
          ],
          city: [
            { required: true, message: 'Ingrese categoria', trigger: 'change' }
          ],
          status: [
            { required: true, message: 'Please select a status', trigger: 'change' }
          ],
          civils: [
            { required: true, message: 'INgrese el estatus del proyecto', trigger: 'change' }
          ],
          sex: [
            { required: true, message: 'Please select a gender', trigger: 'change' }
          ],
          link: [
           { required: true, message: 'ingresa el link', trigger: 'blur' }
          ],
          address: [
            { required: true, message: 'porfavor ingrese descripcion', trigger: 'blur' }
          ] 
          },
        }
      
        }, //Aqui termina la funcion data
      computed: {  //Esta funcion validará si se muestran o no algunos componentes
        validar: function (){
          return this.tabPosition != 'provider'
        },
      },
  
      methods: {
        addItem: function () { //agregar campos insertados
          this.gridData.push({
          name:      this.ruleForm3.name,
          last:      this.ruleForm3.last,
          city:      this.ruleForm3.city,
          status:    this.ruleForm3.status,
          civils:    this.ruleForm3.civils,
          sex:       this.ruleForm3.sex,
          link:      this.ruleForm3.link,
          address:   this.ruleForm3.address
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
    .customers {
      background-color: #E9EEF3;
      color: #333;
      width: 100%;
      margin-right: 5%;
    }
</style>
