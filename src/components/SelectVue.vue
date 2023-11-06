<template>
    <div class="user-information__select">
      <select v-model="role" placeholder="Повторите пароль" v-bind:class="[this.isBadRoleProps ? 'bad-form' : '', 'select-form']" v-on:change="isGoodFormRole">
        <option disabled value="">Должность</option>
        <option value="1">Тестировщик</option>
        <option value="2">Стажер-программист</option>
        <option value="3">Программист</option>
        <option value="4">Старший Программист</option>
      </select>
    </div>
    <p v-bind:class="[this.isBadRoleProps ? 'erron-forms-select' : 'good-forms-select']">выберите должность</p>
</template>
  
  <script>

    export default {
      name: 'SelectVue',
      emits: ['select-updated'],
      props: ['isBadRoleProps'],
      methods: {
        isGoodFormRole() {
          this.isBadRole = false;
          this.$emit('select-updated', this.role);
        },
      },
      data() {
        return {
          role: "",
        };
      },
    };
  </script>
  
<style>
  
  .user-information__select {
    display: flex;
    justify-content: right;
  }

  .bad-form {
    border: 1px solid red;
  }

  .select-form {
    width: 450px;
    height: 35px;
    border: 1px solid rgb(209, 209, 209);
    color: gray;
    border-radius: 11px;
    font-size: 16px;
    padding: 0 0 0 10px;
    margin: 12px 23px 0 0;
  }

  .good-forms-select {
    visibility: hidden;
    padding: 0;
    margin: 0 0 0 480px;
  }

  .erron-forms-select {
    visibility: inherit;
    padding: 0;
    margin: 0 0 0 480px;
  }
    
</style>
  