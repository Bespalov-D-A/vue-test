<script setup>
  import HelloWorld from './components/HelloWorld.vue'
  import UsersTable from './components/UsersTable/'
</script>

<template>
  <div class="main-wrapper">
    <header>
      <div class="header">
        <HelloWorld msg="Vue demostration" />
      </div>
    </header>

    <main class="main">
      <UsersTable />
    </main>
  </div>
</template>

<style scoped>
  header {
    line-height: 1.5;
  }
</style>
