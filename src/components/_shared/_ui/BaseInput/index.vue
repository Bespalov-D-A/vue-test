<template>
  <div class="input-wrapper">
    <input
      :type="inputType"
      class="input"
      @input="updateValue"
      :value="localValue"
      :placeholder="placeholder"
    />
  </div>
</template>

<script>
  export default {
    name: 'BaseInput',
    props: ['customChange', 'value', 'placeholder', 'inputType'],

    data() {
      return {
        localValue: this.value
      }
    },
    methods: {
      updateValue(event) {
        let newValue = event.target.value
        this.localValue = newValue
        this.$emit('update:value', newValue)
      },
      handleInput(event) {
        console.log(event.data)
      }
    }
  }
</script>

<style scoped>
  .input-wrapper {
    position: relative;
    width: 100%;
    height: 60px;
  }

  .input {
    width: 100%;
    padding: 10px;
    font-size: 16px;
    border: 0;
    border-bottom: 1px solid #ccc;
    transition: border-color 0.3s ease;
  }

  .input:focus {
    outline: none;
    border-color: #007bff;
  }
</style>
