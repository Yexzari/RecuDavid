<template>
    <div>
  
      <b-col cols="9" style="margin-left: 320px">
        <router-view />
      </b-col>
  
      <div class="overflow-auto">
        <b-pagination
          v-model="currentPage"
          :total-rows="rows"
          :per-page="perPage"
          aria-controls="my-table"
        ></b-pagination>
  
        <p class="mt-3">Current Page: {{ currentPage }}</p>
  
        <b-table
          id="my-table"
          :items="stude"
          :per-page="perPage"
          :current-page="currentPage"
          small
          :fields="fields"
      :sort-by.sync="sortBy"
      :sort-desc.sync="sortDesc"
        ></b-table>
  
        <formulario @formSubmitted="handleFormSubmitted" />
  
      </div>
    </div>
  </template>
  
  <script>
  import Formulario from './Formulario.vue';

  export default {
    components: {
    Formulario,
  },
    data() {
      return {
        sortBy: 'age',
        sortDesc: false,
        fields: [
          { key: 'name', sortable: true },
          { key: 'edad', sortable: true },
          { key: 'cuatri', sortable: true },
          { key: 'carrera', sortable: false }
        ],
        items: [
          {
            text: 'Formulario',
            href: '#',
            to: 'Formulario',
          },
          {
            text: 'Inicio',
            href: '#',
          },
        ],
        perPage: 3,
        currentPage: 1,
        stude: [ {
        "name": "Juan",
        "edad": 20,
        "cuatri": 3,
        "carrera": "Ingeniería Civil",
        "ID": 1
    },
    {
        "name": "María",
        "edad": 22,
        "cuatri": 5,
        "carrera": "Medicina",
        "ID": 2
    },
    {
        "name": "Luis",
        "edad": 19,
        "cuatri": 2,
        "carrera": "Psicología",
        "ID": 3
    },
    {
        "name": "Ana",
        "edad": 21,
        "cuatri": 4,
        "carrera": "Derecho",
        "ID": 4
    },
    {
        "name": "Pedro",
        "edad": 23,
        "cuatri": 6,
        "carrera": "Administración de Empresas",
        "ID": 5
    }],
      };
    },
    computed: {
      rows() {
        return this.stude.length;
      },
    },
    methods: {
  handleFormSubmitted(formData) {
    console.log('Formulario enviado:', formData);

    const newId = this.stude.length + 1;
    console.log('Nuevo ID:', newId);

    this.stude.push({ ID: newId, ...formData });
    console.log('stude actualizado:', this.stude);
  },
},

  };
  </script>
  
  <style>
    /* Estilos adicionales si es necesario */
  </style>
  