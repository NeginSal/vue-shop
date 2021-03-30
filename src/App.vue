<template>
  <div id="nav">
    <router-link to="/">Home</router-link> |
    <router-link to="/about">About</router-link>
  </div>
  <div class="container">
    <router-view />
  </div>
</template>

<style lang="scss">
@import 'node_modules/bootstrap/scss/bootstrap';
</style>
