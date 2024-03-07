<template>
<div>
    <h1>Inicio</h1>
    <b-breadcrumb :items="items"></b-breadcrumb></div>
        

</template>

<script>
export default {
data() {
      return {
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
        stude: [],
      };
    },
}
</script>

<style>

</style>