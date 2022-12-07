<template>
    <footer>
      <ul>
        <li>Productos</li>
        <li v-if="!isMobile">Servicios</li>
        <li v-else>Servicios Mobile</li>
        <li>Contacta</li>
      </ul>
    </footer>
  </template>
  
  <script>
  export default {
    data() {
      return {
        isMobile: true,
      };
    },
  };
  </script>
  
  <style scoped>
  ul {
    display: flex;
    gap: 4em;
  }
  li {
    list-style-type: none;
  }
  </style>