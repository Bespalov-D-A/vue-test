<script setup>
  import BaseCheckbox from './../../../_shared/_ui/BaseCheckbox/index.vue'
  import BaseInput from './../../../_shared/_ui/BaseInput/'
</script>

<template>
  <div class="users-table-row">
    <div class="users-table-column users-table-column--checkbox">
      <BaseCheckbox
        :handleChangeCheckBox="changeCheckBox"
        :isChecked="isChecked"
      />
    </div>
    <div v-if="!isEdit" class="users-table-column users-table-column--name">
      {{ name }}
    </div>
    <div v-if="isEdit" class="users-table-column users-table-column--name">
      <BaseInput
        :placeholder="'name'"
        :value.sync="userName"
        :customChange="inputHandleChange"
        @update:value="userName = $event"
      />
    </div>
    <div v-if="!isEdit" class="users-table-column users-table-column--lastname">
      {{ lastName }}
    </div>
    <div v-if="isEdit" class="users-table-column users-table-column--lastName">
      <BaseInput
        :placeholder="'last name'"
        :value.sync="userLastName"
        :customChange="inputHandleChange"
        @update:value="userLastName = $event"
      />
    </div>

    <div v-if="!isEdit" class="users-table-column users-table-column--years">
      {{ years }}
    </div>
    <div v-if="isEdit" class="users-table-column users-table-column--years">
      <BaseInput
        :inputType="'number'"
        :placeholder="'years'"
        :value.sync="userYears"
        :customChange="inputHandleChange"
        @update:value="userYears = $event"
      />
    </div>

    <div v-if="!isEdit" class="users-table-column users-table-column--age">
      {{ age }}
    </div>
    <div v-if="isEdit" class="users-table-column users-table-column--age">
      <BaseInput
        :inputType="'number'"
        :placeholder="'age'"
        :value.sync="userAge"
        :customChange="inputHandleChange"
        @update:value="userAge = $event"
      />
    </div>

    <div v-if="!isEdit" class="users-table-column users-table-column--address">
      {{ address }}
    </div>
    <div v-if="isEdit" class="users-table-column users-table-column--address">
      <BaseInput
        :placeholder="'address'"
        :value.sync="userAddress"
        :customChange="inputHandleChange"
        @update:value="userAddress = $event"
      />
    </div>

    <div
      v-if="!isEdit"
      @click="toggleIsEdit"
      class="users-table-column users-table-column--edit"
    >
      ✎
    </div>
    <div
      v-if="isEdit"
      :class="{ 'c-green': isEdit }"
      @click="toggleIsEdit"
      class="users-table-column users-table-column--edit"
    >
      ok
    </div>
  </div>
</template>

<script>
  export default {
    name: 'UserTableLine',
    props: {
      name: {
        type: String,
        required: true
      },
      lastName: {
        type: String,
        required: true
      },
      years: {
        type: Number,
        required: true
      },
      age: {
        type: Number,
        required: true
      },
      address: {
        type: String,
        required: true
      },
      index: { type: Number, required: true },
      id: { type: String, required: true },
      isChecked: { required: true },
      handleChangeCheckBox: { required: true },
      updateUser: { required: true }
    },
    data() {
      return {
        isEdit: false,
        userName: this.name,
        userLastName: this.lastName,
        userYears: this.years,
        userAge: this.age,
        userAddress: this.address
      }
    },
    watch: {
      userName(newValue) {
        console.log(this.userName)
      }
    },
    methods: {
      changeCheckBox() {
        this.handleChangeCheckBox(this.id)
      },
      toggleIsEdit() {
        if (this.isEdit) {
          let obj = {
            name: this.userName,
            lastName: this.userLastName,
            years: this.userYears,
            age: this.userAge,
            address: this.userAddress
          }
          this.updateUser(this.id, obj)
        }
        this.isEdit = !this.isEdit
      },
      inputHandleChange(event) {
        console.log(event)
      }
    },
    computed: {},
    mounted() {}
  }
</script>

<style scoped>
  .usertableline {
    border: solid 1px red;
  }
</style>
