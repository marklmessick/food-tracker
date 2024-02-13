<script setup>
import HelloWorld from './components/HelloWorld.vue'
</script>

<template>
  <!-- Create a header/navigation menu -->



  <!-- <div class="header">
    <nav>
      <div>
        <a href="index.html">
          <img src="./assets/soilshare_logo_alt.png" class="logo" alt="Soilshare logo" />
        </a>
      </div>
    </nav>
  </div> -->

  <HelloWorld/>
</template>

<style scoped>

.header {
  background-color: #cbb38b;
  padding: 1em;
  text-align: center;
  margin-bottom: 1em;
}
.logo {
  height: 7em;
  /* padding: 1.5em; */
  will-change: filter;
  transition: filter 300ms;
  padding-top: -3000px;
}
.logo:hover {
  filter: drop-shadow(0 0 2em #479c4c);
}

</style>
