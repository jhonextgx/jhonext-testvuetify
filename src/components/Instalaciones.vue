<template>
  <v-container>
    <v-layout
      text-center
      wrap
    >
      <v-flex mb-4>
          <v-card
              class="mx-auto"              
            >
              <v-card-title
                class="blue lighten-3 white--text"
              >
                <h3>Instalaciones</h3>
              </v-card-title>
              <v-card-text><!-- contenido del vcard-->               
                <v-row>
                      <v-col
                        v-for="(next, i) in filtroVcard"
                        :key="i"                        
                        cols="12"
                        sm="4"
                      >
                      <v-text-field :label="next.label"></v-text-field>
                      </v-col>
                </v-row>                
              </v-card-text>
          <v-card
            class="d-flex flex-row-reverse"
            color="grey lighten-2"
            flat
            tile
          >    
              <v-card        
              outlined
              tile
              >
                <v-btn color="success" >Limpiar</v-btn>
              </v-card>
              <v-card        
              outlined
              tile
              >
                <v-btn color="success" >Filtrar</v-btn>
              </v-card>              
          </v-card>               

            </v-card>
      </v-flex>
      <v-flex mb-4>
          <v-card
              class="mx-auto"              
            >
              <v-card-text><!-- contenido del vcard-->
                <!--<v-data-table dense :headers="headers" :items="elementosTable" item-key="name" class="elevation-1">                 
                <template v-slot:default-header                
                >                  
                </template>                   
                <template v-slot:item.action="{ item }">
                  <v-icon medium
                    class="mr-2"
                    @click="actions(item)"                  
                  >mdi-file-document-box-outline</v-icon>                 
                  <v-icon
                    medium
                    color="green darken-2"
                    class="mr-2"
                    @click="actions(item)"                 
                  >
                    mdi-call-split
                  </v-icon>
                </template>               
                </v-data-table>   -->           
                <v-simple-table dense>
                    <template v-slot:default>
                      <thead>
                        <tr>
                          <th class="white--text" v-for="item in headers" :key="item.value">{{item.text}}</th>                         
                        </tr>
                      </thead>
                      <tbody>
                        <tr :class="{'warningClass':colocarStatus(item),'errorClass':colocarStatus(item)==false}" v-for="item in elementosTable" :key="item.name">
                          <td><v-btn small  :color="getColor (item.elementos)" dark></v-btn></td>
                          <td><v-icon medium
                                class="mr-2"
                                @click="actions(item)"                  
                                >mdi-file-document-box-outline</v-icon>                 
                          </td>
                          <td>
                              <v-icon
                                medium
                                color="green darken-2"
                                class="mr-2"
                                @click="actions(item)"                 
                              >
                                mdi-call-split
                              </v-icon>
                          </td>                                                   
                          <td>{{ item.codigo }}</td>
                          <td>{{ item.nombre }}</td>
                          <td>{{ item.gm }}</td>
                          <td>{{ item.tm }}</td>
                          <td>{{ item.jz }}</td>
                          <td>{{ item.ej }}</td>
                          <td>{{ item.direccion }}</td>
                          <td>{{ item.elementos }}</td>
                          <td><small>{{ item.ultimat }}</small></td>                          
                        </tr>
                      </tbody>
                      <tfoot>
                        <tr>
                          <td colspan="11">
                            <v-row class="mb-2">
                                  <span class="group pa-2">
                                    <v-icon
                                      medium
                                      color="white darken-2"
                                      class="mr-2"
                                       @click="actions(item)"
                                      >mdi-skip-backward</v-icon>                                      
                                    <v-icon  @click="actions(item)" color="white darken-2">mdi-chevron-left</v-icon>
                                    1    /    {{elementosTable.length}}
                                    <v-icon  @click="actions(item)" color="white darken-2">mdi-chevron-right</v-icon>
                                    <v-icon  @click="actions(item)"  dark>mdi-skip-forward</v-icon>
                                  </span>                                  
                            </v-row> 
                          </td>
                          <td>                            
                              {{elementosTable.length}} Registros                                                   
                          </td>                          
                        </tr>
                      </tfoot>                      
                    </template>
                  </v-simple-table>                
              </v-card-text>

          <v-card
            class="d-flex flex-row-reverse"
            color="grey lighten-2"
            flat
            tile
          >    
              <v-card        
              outlined
              tile
              >
                <v-btn color="success" >PDF</v-btn>
              </v-card>
              <v-card        
              outlined
              tile
              >
                <v-btn color="success" >EXCEL</v-btn>
              </v-card>              
          </v-card>                           
        </v-card>
      </v-flex>      
    </v-layout>
  </v-container>
</template>

<script>
export default {
  name: 'HelloWorld',

  data: () => ({
    filtroVcard: [
      {
        label: 'Código de Intalación',
        input: 'inst_codigo',
      },
      {
        label: 'Nombre Instalación',
        input: 'inst_nombre',
      },
      {
        label: 'Municipio',
        input: 'inst_municipio',
      },
      {
        label: 'Provincia',
        input: 'inst_provincia',
      },
      {
        label: 'Gestor de Mantenimiento',
        input: 'inst_gestor_mantto',
      },
      {
        label: 'Jefe de Zona',
        input: 'inst_jefezona',
      },                  
    ],
      elementosTable: [
        {
          codigo: '001',
          nombre: 'Instalación',
          gm: "GM",
          tm: "TM",
          jz: "JZ",
          ej: "EJ",
          direccion: 'Calle, Avda, Paseo, PLaza de la instalacion',
          elementos: 22,
          ultimat: "06/12/2019 19:20:23"
        },
        {
          codigo: '002',
          nombre: 'Instalación',
          gm: "GM",
          tm: "TM",
          jz: "JZ",
          ej: "EJ",
          direccion: 'Calle, Avda, Paseo, PLaza de la instalacion',
          elementos: 21,
          ultimat: "06/12/2019 19:20:23"
        },
        {
          codigo: '003',
          nombre: 'Instalación',
          gm: "GM",
          tm: "TM",
          jz: "JZ",
          ej: "EJ",
          direccion: 'Calle, Avda, Paseo, PLaza de la instalacion',
          elementos: 24,
          ultimat: "06/12/2019 19:20:23"
        },
        {
          codigo: '004',
          nombre: 'Instalación',
          gm: "GM",
          tm: "TM",
          jz: "JZ",
          ej: "EJ",
          direccion: 'Calle, Avda, Paseo, PLaza de la instalacion',
          elementos: 16,
          ultimat: "06/12/2019 19:20:23"
        },
        {
          codigo: '005',
          nombre: 'Instalación',
          gm: "GM",
          tm: "TM",
          jz: "JZ",
          ej: "EJ",
          direccion: 'Calle, Avda, Paseo, PLaza de la instalacion',
          elementos: 43,
          ultimat: "06/12/2019 19:20:23"
        },
        {
          codigo: '006',
          nombre: 'Instalación',
          gm: "GM",
          tm: "TM",
          jz: "JZ",
          ej: "EJ",
          direccion: 'Calle, Avda, Paseo, PLaza de la instalacion',
          elementos: 21,
          ultimat: "06/12/2019 19:20:23"
        },
        {
          codigo: '007',
          nombre: 'Instalación',
          gm: "GM",
          tm: "TM",
          jz: "JZ",
          ej: "EJ",
          direccion: 'Calle, Avda, Paseo, PLaza de la instalacion',
          elementos: 32,
          ultimat: "06/12/2019 19:20:23"
        },
        {
          codigo: '008',
          nombre: 'Instalación',
          gm: "GM",
          tm: "TM",
          jz: "JZ",
          ej: "EJ",
          direccion: 'Calle, Avda, Paseo, PLaza de la instalacion',
          elementos: 22,
          ultimat: "06/12/2019 19:20:23"
        },
        {
          codigo: '009',
          nombre: 'Instalación',         
          gm: "GM",
          tm: "TM",
          jz: "JZ",
          ej: "EJ",
          direccion: 'Calle, Avda, Paseo, PLaza de la instalacion',
          elementos: 26,
          ultimat: "06/12/2019 19:20:23"
        },
        {
          codigo: '010',
          nombre: 'Instalación',
          gm: "GM",
          tm: "TM",
          jz: "JZ",
          ej: "EJ",
          direccion: 'Calle, Avda, Paseo, PLaza de la instalacion',
          elementos: 12,
          ultimat: "06/12/2019 19:20:23"
        },
      ],
      headers: [       
        { text: '', value: 'action1', sortable: false },
        { text: '', value: 'action2', sortable: false },        
        { text: '', value: 'action3', sortable: false }, 
        {
          text: 'Cód.',
          align: 'left',
          sortable: false,
          value: 'codigo',
        },
        { text: 'Nombre', value: 'nombre' },
        { text: 'GM', value: 'gm' },
        { text: 'TM', value: 'tm' },
        { text: 'JZ', value: 'jz' },
        { text: 'EJ', value: 'ej' },
        { text: 'Dirección', value: 'direccion' },
        { text: 'Elementos', value: 'elementos' },
        { text: 'Última transacción', value: 'ultimat' },
      ],            
  }),
    methods: {
      getColor (elemento) {
        if (elemento == 21) return 'yellow'
        else if (elemento == 16) return 'red'
        else return 'green'
      },
      colocarStatus(item){         
          if(item.elementos === 21) return true
          else if(item.elementos === 16) return false                 
      },
      actions(item){
          alert("Actions @jhonext");
      },
    },  
}
</script>
<style>
 th{
   color:white;
   background-color: #72AC48;   
 }
 tfoot{
    color:white;
    background-color: #72AC48; 
 }
 .warningClass{
   background-color: #FFC000;
 }
  .errorClass{
   background-color: #FE0000;
 }
 .sucessClass{
   background-color: #00B050;
 }
</style>
/*@Jhonext */