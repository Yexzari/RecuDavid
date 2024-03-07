<template>
    <div>
      <b-breadcrumb :items="items"></b-breadcrumb>
      <b-form @submit="onSubmit" @reset="onReset" v-if="show">
        <b-form-group id="input-group-2" label="Nombre:" label-for="input-2">
          <b-form-input
            id="input-2"
            v-model="form.name"
            placeholder="Enter name"
            required
            @input="validateNonNumericInput('name')"
          ></b-form-input>
        </b-form-group>
        <b-form-group id="input-group-2" label="Edad:" label-for="input-3">
          <b-form-input
            id="input-3"
            v-model="form.edad"
            placeholder="Ingresa Edad"
            required
            type="number"
            min="0"
            max="100"
            @input="validateNumericInput('edad')"
          ></b-form-input>
        </b-form-group>
        <b-form-group id="input-group-2" label="Cuatri:" label-for="input-4">
          <b-form-input
            id="input-4"
            v-model="form.cuatri"
            placeholder="Ingresa Cuatri"
            required
            type="number"
            min="0"
            max="12"
            @input="validateNumericInput('cuatri')"
          ></b-form-input>
        </b-form-group>
        <b-form-group id="input-group-2" label="Carrera:" label-for="input-5">
          <b-form-input
            id="input-5"
            v-model="form.carrera"
            placeholder="Ingresa Carrera"
            required
            @input="validateNonNumericInput('carrera')"
          ></b-form-input>
        </b-form-group>
        <b-button type="submit" variant="primary">Registrar</b-button>
      </b-form>
    </div>
  </template>
  
  <script>
  export default {
    data() {
      return {
        items: [
          {
            text: 'Inicio',
            href: '#',
            to: 'Inicio',
          },
          {
            text: 'Formulario',
            href: '#',
          },
        ],
        form: {
          edad: '',
          name: '',
          edad: '',
          cuatri: '',
          carrera: '',
        },
        show: true,
      };
    },
    methods: {
          handleFormSubmitted(formData) {
    console.log('Formulario enviado:', formData);

    const newId = this.stude.length + 1;
    console.log('Nuevo ID:', newId);

    this.stude.push({ ID: newId, ...formData });
    console.log('stude actualizado:', this.stude);
  },
      onSubmit(event) {
        event.preventDefault();
        // Validar que "Nombre" y "Carrera" no contengan números
        if (
          this.isNumeric(this.form.edad) &&
          this.isNumeric(this.form.cuatri) &&
          this.isNonNumeric(this.form.name) &&
          this.isNonNumeric(this.form.carrera)
        ) {
          // Emitir evento con los datos del formulario
          this.$emit('formSubmitted', { ...this.form });
        } else {
          alert('Por favor, ingresa valores válidos en los campos.');
        }
      },
      onReset(event) {
        event.preventDefault();
        if (
          !this.isNumeric(this.form.edad) ||
          !this.isNumeric(this.form.cuatri) ||
          !this.isNonNumeric(this.form.name) ||
          !this.isNonNumeric(this.form.carrera)
        ) {
          alert('Por favor, ingresa valores válidos en los campos.');
        }
      },
      validateNumericInput(field) {
        // Función para validar que solo se ingresen valores numéricos
        if (!this.isNumeric(this.form[field])) {
          this.form[field] = this.form[field].replace(/[^0-9]/g, '');
        }
      },
      validateNonNumericInput(field) {
        // Función para validar que no se ingresen valores numéricos
        if (this.isNumeric(this.form[field])) {
          this.form[field] = this.form[field].replace(/[0-9]/g, '');
        }
      },
      isNumeric(value) {
        // Función para verificar si el valor es numérico
        return /^\d+$/.test(value);
      },
      isNonNumeric(value) {
        // Función para verificar si el valor no es numérico
        return /^[^\d]+$/.test(value);
      },
    },
  };
  </script>
  
  <style>
    /* Estilos adicionales si es necesario */
  </style>
  