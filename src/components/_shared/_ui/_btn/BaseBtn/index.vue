<template>
  <button class="btn" :class="btnClass()" @click="handleClick">
    {{ btnText }}
  </button>
</template>

<script>
  export default {
    name: 'BaseBtn',
    props: {
      handleClick: { type: Function },
      btnType: { type: String, default: 'default' },
      btnText: { type: String, required: true }
    },
    methods: {
      btnClass() {
        return {
          'btn--default': this.btnType === 'default',
          'btn--danger': this.btnType === 'danger',
          'btn--success': this.btnType === 'success'
        }
      }
    }
  }
</script>

<style>
  .btn {
    min-width: 100px;
    padding: 10px 20px;
    border-radius: 4px;
    font-size: 16px;
    transition: background-color 0.3s;
    border: none;
    color: white;
    cursor: pointer;
  }
</style>
