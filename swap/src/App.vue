<template>
  <v-app>
    <v-img height="200" src="../../public/Logo/Swap_green.svg" id="logo" />
    <v-main>
      <HomePage />
    </v-main>
    <footer>
      <footer-component id="footer"/>
    </footer>
  </v-app>
</template>

<script setup>

//
</script>

<style>
#logo {
  position: absolute;
  top: -45px;
  left: -45px;
  width: 300px;
  padding: 0;
}

#footer{
  margin-top: 15px;
  padding: 0;
}
</style>
