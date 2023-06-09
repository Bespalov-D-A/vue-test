<script setup>
  import BaseInput from './../../_shared/_ui/BaseInput/'
  import BaseBtn from './../../_shared/_ui/_btn/BaseBtn/'
  import { randomString } from './../../../data/randomString.js'
</script>

<template>
  <div @click="localClick" class="adduser">
    <h2 class="adduser__title">Add user</h2>
    <BaseInput
      :placeholder="'name'"
      :value.sync="userName"
      :customChange="inputHandleChange"
      @update:value="userName = $event"
    />
    <BaseInput
      :placeholder="'last name'"
      :value.sync="userLastName"
      :customChange="inputHandleChange"
      @update:value="userLastName = $event"
    />
    <BaseInput
      :inputType="'number'"
      :placeholder="'years'"
      :value.sync="userYears"
      :customChange="inputHandleChange"
      @update:value="userYears = $event"
    />
    <BaseInput
      :inputType="'number'"
      :placeholder="'age'"
      :value.sync="userAge"
      :customChange="inputHandleChange"
      @update:value="userAge = $event"
    />
    <BaseInput
      :placeholder="'address'"
      :value.sync="userAddress"
      :customChange="inputHandleChange"
      @update:value="userAddress = $event"
    />
    <div class="adduser__footer">
      <BaseBtn :btnText="'Add user'" :handleClick="localHandle" />
    </div>
  </div>
</template>

<script>
  export default {
    name: 'AddUser',
    props: ['handleAddUser'],
    data() {
      return {
        userName: '',
        userLastName: '',
        userYears: 0,
        userAge: 0,
        userAddress: ''
      }
    },
    methods: {
      localClick(e) {
        e.stopPropagation()
      },
      inputHandleChange(event) {
        console.log(this.userName)
        console.log(event)
      },
      localHandle() {
        const obj = {
          name: this.userName,
          lastName: this.userLastName,
          years: this.userYears,
          age: this.userAge,
          address: this.userAddress,
          id: randomString()
        }

        //       this.userName = ''
        //       this.userLastName = ''
        //       this.userYears = 0
        //       this.userAge = 0
        //       this.userAddress = ''

        this.handleAddUser(obj)
      }
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
  .adduser {
    display: flex;
    flex-flow: column nowrap;
    justify-content: center;
    min-width: 600px;
    padding: 24px;
    border-radius: 18px;
    background: #fff;
  }
  .adduser__title {
    margin-bottom: 12px;
  }
  .adduser__footer {
    display: flex;
    justify-content: flex-end;
  }
</style>
