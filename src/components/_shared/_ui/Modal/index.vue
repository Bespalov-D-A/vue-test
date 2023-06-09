<template>
  <div @click="closeModal" class="modal">
    <slot></slot>
  </div>
</template>

<script>
  export default {
    name: 'Modal',
    props: ['isOpenModal', 'closeModal'],
    data() {
      return {
        // Ваши данные
      }
    },
    methods: {
      // Ваши методы
    },
    computed: {
      // Ваши вычисляемые свойства
    },
    mounted() {
      // Логика, выполняемая после монтирования компонента
    }
  }
</script>

<style scoped>
  .modal {
    position: absolute;
    left: 0;
    top: 0;
    display: flex;
    justify-content: center;
    align-items: center;
    width: 100%;
    height: 100%;
    background: rgba(0, 0, 0, 0.5);
  }
</style>
