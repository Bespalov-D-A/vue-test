<template>
  <label class="checkbox-container">
    <input
      :checked="isChecked"
      type="checkbox"
      @change="handleChangeCheckBox"
    />
    <span class="checkmark"></span>
    {{ label }}
    {{ isChecked }}
  </label>
</template>

<script>
  export default {
    name: 'Checkbox',
    props: ['label', 'value', 'handleChangeCheckBox', 'isChecked']
  }
</script>

<style scoped>
  .checkbox-container {
    display: inline-flex;
    align-items: center;
    cursor: pointer;
    font-size: 14px;
  }

  .checkbox-container input {
    opacity: 0;
    position: absolute;
  }

  .checkmark {
    display: inline-block;
    width: 16px;
    height: 16px;
    border: 2px solid #ccc;
    border-radius: 3px;
    margin-right: 8px;
    background-color: transparent;
    transition: background-color 0.3s ease;
  }

  .checkbox-container:hover .checkmark {
    border-color: #888;
  }

  .checkbox-container input:checked + .checkmark {
    background-color: #3399ff;
  }
</style>
