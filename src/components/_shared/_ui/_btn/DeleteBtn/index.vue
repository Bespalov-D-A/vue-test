<template>
  <button class="delete-button" @click="handleDelete">Delete</button>
</template>

<script>
  export default {
    name: 'DeleteButton',
    props: ['handleDelete']
  }
</script>

<style>
  .delete-button {
    min-width: 100px;
    padding: 10px 20px;
    border-radius: 4px;
    font-size: 16px;
    transition: background-color 0.3s;
    background-color: #f44336;
    border: none;
    color: white;
    cursor: pointer;
  }

  .delete-button:hover {
    background-color: #d32f2f;
  }

  .delete-button:active {
    background-color: #b71c1c;
  }
</style>
