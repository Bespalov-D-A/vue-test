<script setup>
  import DeleteBtn from './../_shared/_ui/_btn/DeleteBtn/'
  import BaseBtn from './../_shared/_ui/_btn/BaseBtn/'
  import UserTableLine from './_children/UserTableLine/'
  import { users } from './../../data/users'
  import AddUser from './AddUser/'
  import Modal from './../_shared/_ui/Modal/'
</script>

<template>
  <Modal v-if="isOpenModal" :isOpenModal="isOpenModal" :closeModal="closeModal">
    <AddUser :handleAddUser="handleAddUser" />
  </Modal>
  <div class="users-table-wrap">
    <div class="users-table-wrap__header">
      <DeleteBtn :handleDelete="removeManyUsers" />
      <BaseBtn
        :btnType="'success'"
        :btnText="'Add user'"
        :handleClick="openModal"
      />
    </div>
    <div class="users-table">
      <div class="users-table-row users-table-row--header">
        <div class="users-table-column users-table-column--checkbox">
          <!-- <BaseCheckbox /> -->
        </div>
        <div class="users-table-column users-table-column--name">Имя</div>
        <div class="users-table-column users-table-column--lastname">
          Фамилия
        </div>
        <div class="users-table-column users-table-column--years">Стаж</div>
        <div class="users-table-column users-table-column--age">Возраст</div>
        <div class="users-table-column users-table-column--address">Адрес</div>
        <div class="users-table-column users-table-column--edit"></div>
      </div>

      <UserTableLine
        v-for="(user, index) in mountedUsers"
        :key="user.id"
        :name="user.name"
        :lastName="user.lastName"
        :years="user.years"
        :age="user.age"
        :address="user.address"
        :index="index"
        :id="user.id"
        :isChecked="checkSelected(user.id)"
        :handleChangeCheckBox="handleChangeCheckBox"
        :updateUser="updateUser"
      />
    </div>
  </div>
</template>

<script>
  export default {
    name: 'UserTableLine',
    data() {
      return {
        mountedUsers: users,
        selectedUsers: [],
        isOpenModal: false
      }
    },

    methods: {
      selectUser(id) {
        this.selectedUsers.push(id)
      },
      unselectUser(id) {
        const identifer = this.selectedUsers.findIndex(item => item === id)
        if (identifer !== -1) this.selectedUsers.splice(identifer, 1)
      },
      checkSelected(id) {
        const identifer = this.selectedUsers.find(item => item === id)
        return identifer
      },
      handleChangeCheckBox(id) {
        if (this.checkSelected(id)) this.unselectUser(id)
        else this.selectUser(id)
      },
      removeUser(id) {
        const identifer = this.mountedUsers.findIndex(item => item.id === id)
        if (identifer !== -1) this.mountedUsers.splice(identifer, 1)
      },
      removeManyUsers() {
        this.selectedUsers.forEach(userId => this.removeUser(userId))
      },
      updateUser(id, obj) {
        const identifer = this.mountedUsers.findIndex(item => item.id === id)
        if (identifer !== -1) {
          this.mountedUsers[identifer].name = obj.name
          this.mountedUsers[identifer].lastName = obj.lastName
          if (!isNaN(Number(obj.years)))
            this.mountedUsers[identifer].years = Number(obj.years)
          if (!isNaN(Number(obj.age)))
            this.mountedUsers[identifer].age = Number(obj.age)
          this.mountedUsers[identifer].address = obj.address
        }
      },
      handleAddUser(obj) {
        this.closeModal()
        this.mountedUsers.push(obj)
      },
      closeModal(e) {
        this.isOpenModal = false
      },

      openModal() {
        this.isOpenModal = true
      }
    }
  }
</script>

<style scoped></style>
