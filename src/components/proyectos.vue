<template>
    <div class="proyectos">
       <!---->
        <!--Inicia formulario form-->
              
              
        <div>
        <el-container>
                    <el-aside width="200px" style="color: #303133"><h1>MENU</h1>
                     <!-- ======================cascada====================== -->
                      <el-cascader
                        :options="options"
                        :show-all-levels="false"
                    ></el-cascader>
                    <!-- ======================botones====================== -->
                      <el-button type="primary">Top Proyectos</el-button>
                        <el-button type="primary">Mas Recientes</el-button>
                          <el-button type="primary">Nuevas Versiones</el-button>
                    </el-aside>
            <el-container>
                <el-header style="color: #303133"><h2>PROYECTOS EXISTENTES</h2></el-header>
                    
                    <el-main>
                        <div style="margin-top: 15px;">
                        <el-input placeholder="Buscar en Categoria" v-model="input5" class="input-with-select">
                            <el-select v-model="select" slot="prepend" placeholder="Select">
                                <el-option label="Navegadores y Sistemas Operativos" value="Navegadores y Sistemas Operativos"></el-option>
                                <el-option label="Plataformas móviles" value="Plataformas móviles"></el-option>
                                <el-option label="Lenguajes de programación" value="Lenguajes de programación"></el-option>
                                <el-option label="Aplicaciones de trabajo" value="Aplicaciones de trabajo"></el-option>
                            </el-select>
                            <el-button slot="append" icon="el-icon-search"></el-button>
                        </el-input>
                        </div>
                    </el-main>
                
                <el-footer style="color: #303133"><h2> footer</h2></el-footer>
            
            </el-container>
        </el-container>
 
        </div>


    </div>
</template>


<script>
import EditableCell from "./EditableCell.vue";
export default {
     data() {
    return {
      input3: '',
      input4: '',
      input5: '',
      select: ''
    }
  },
  //este es el botton de seleccionar categoria en cascada
  data() {
      return {
        options: [{
            //LABEL ES EL NOMBRE DE CATEGORIA
            //======================rama0======================
          value: 'guide',
          label: 'Navegadores y Sistemas Operativos', 
          children: [{
            value: 'disciplines',
            label: 'Disciplines',
            children: [{
              value: 'consistency',
              label: 'Consistency'
            }, {
              value: 'feedback',
              label: 'Feedback'
            }, {
              value: 'efficiency',
              label: 'Efficiency'
            }, {
              value: 'controllability',
              label: 'Controllability'
            }]
          }, {
            value: 'navigation',
            label: 'Navigation',
            children: [{
              value: 'side nav',
              label: 'Side Navigation'
            }, {
              value: 'top nav',
              label: 'Top Navigation'
            }]
          }],
          
        },{
            //======================rama1======================
          value: 'guide',
          label: 'Plataformas móviles',
          children: [{
            value: 'disciplines',
            label: 'Disciplines',
            children: [{
              value: 'consistency',
              label: 'Consistency'
            }, {
              value: 'feedback',
              label: 'Feedback'
            }, {
              value: 'efficiency',
              label: 'Efficiency'
            }, {
              value: 'controllability',
              label: 'Controllability'
            }]
          }, {
            value: 'navigation',
            label: 'Navigation',
            children: [{
              value: 'side nav',
              label: 'Side Navigation'
            }, {
              value: 'top nav',
              label: 'Top Navigation'
            }]
          }],
          
        }, {
            //  =======================rama2======================
          value: 'component',
          label: 'Lenguajes de programación',
          children: [{
            value: 'basic',
            label: 'Basic',
            children: [{
              value: 'layout',
              label: 'Layout'
            }, {
              value: 'color',
              label: 'Color'
            }, {
              value: 'typography',
              label: 'Typography'
            }, {
              value: 'icon',
              label: 'Icon'
            }, {
              value: 'button',
              label: 'Button'
            }]
          }, {
            value: 'form',
            label: 'Form',
            children: [{
              value: 'radio',
              label: 'Radio'
            }, {
              value: 'checkbox',
              label: 'Checkbox'
            }, {
              value: 'input',
              label: 'Input'
            }, {
              value: 'input-number',
              label: 'InputNumber'
            }, {
              value: 'select',
              label: 'Select'
            }, {
              value: 'cascader',
              label: 'Cascader'
            }, {
              value: 'switch',
              label: 'Switch'
            }, {
              value: 'slider',
              label: 'Slider'
            }, {
              value: 'time-picker',
              label: 'TimePicker'
            }, {
              value: 'date-picker',
              label: 'DatePicker'
            }, {
              value: 'datetime-picker',
              label: 'DateTimePicker'
            }, {
              value: 'upload',
              label: 'Upload'
            }, {
              value: 'rate',
              label: 'Rate'
            }, {
              value: 'form',
              label: 'Form'
            }]
          }, {
            value: 'data',
            label: 'Data',
            children: [{
              value: 'table',
              label: 'Table'
            }, {
              value: 'tag',
              label: 'Tag'
            }, {
              value: 'progress',
              label: 'Progress'
            }, {
              value: 'tree',
              label: 'Tree'
            }, {
              value: 'pagination',
              label: 'Pagination'
            }, {
              value: 'badge',
              label: 'Badge'
            }]
          }, {
            value: 'notice',
            label: 'Notice',
            children: [{
              value: 'alert',
              label: 'Alert'
            }, {
              value: 'loading',
              label: 'Loading'
            }, {
              value: 'message',
              label: 'Message'
            }, {
              value: 'message-box',
              label: 'MessageBox'
            }, {
              value: 'notification',
              label: 'Notification'
            }]
          }, {
            value: 'navigation',
            label: 'Navigation',
            children: [{
              value: 'menu',
              label: 'NavMenu'
            }, {
              value: 'tabs',
              label: 'Tabs'
            }, {
              value: 'breadcrumb',
              label: 'Breadcrumb'
            }, {
              value: 'dropdown',
              label: 'Dropdown'
            }, {
              value: 'steps',
              label: 'Steps'
            }]
          }, {
            value: 'others',
            label: 'Others',
            children: [{
              value: 'dialog',
              label: 'Dialog'
            }, {
              value: 'tooltip',
              label: 'Tooltip'
            }, {
              value: 'popover',
              label: 'Popover'
            }, {
              value: 'card',
              label: 'Card'
            }, {
              value: 'carousel',
              label: 'Carousel'
            }, {
              value: 'collapse',
              label: 'Collapse'
            }]
          }]
        }, {
            //======================rama3======================
          value: 'resource',
          label: 'Aplicaciones de trabajo',
          children: [{
            value: 'axure',
            label: 'Axure Components'
          }, {
            value: 'sketch',
            label: 'Sketch Templates'
          }, {
            value: 'docs',
            label: 'Design Documentation'
          }]
        }]
      };
    },
  
name: 'proyectos',
  components: {
    EditableCell
    }
    
    }
    
</script>


<style>
   .el-header, .el-footer {
    background-color: #9AAAC6;
    color: #333;
    text-align: center;
    line-height: 60px;
  }
  
  .el-aside {
    background-color: rgb(117, 153, 219);
    color: #333;
    text-align: center;
    line-height: 200px;
  }
  
  .el-main {
    background-color: #E9EEF3;
    color: #333;
    text-align: center;
    line-height: 160px;
  }

</style>
