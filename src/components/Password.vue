<template>
    <div class="user-information__password">

      <div>
        <input
          type='password'
          placeholder="Пароль"
          v-bind:class="[this.isBadPasswordProps ? 'bad-form' : '', 'user-information__password_first input-form']"
          v-model="password"
          v-on:change="isGoodFormPasswors"
        />

        <p v-bind:class="[this.isBadPasswordProps ? 'erron-forms' : 'good-forms']">введите пароль</p>

      </div>

      <div>
        <input
          type='password'
          placeholder="Повторите пароль"
          v-bind:class="[this.isBadPasswordRepeatProps ? 'bad-form' : '', 'user-information__password_second input-form']"
          v-model="password_repeat"
          v-on:change="isGoodFormPassworsRepeat"
        />

        <p v-bind:class="[this.isBadPasswordRepeatProps ? 'erron-forms' : 'good-forms']">введите пароль</p>

      </div>



    </div>
</template>
  
  <script>
    export default {
      name: 'Password',
      emits: ['password-updated', 'password-repeat-updated'],
      props: ['isBadPasswordProps', 'isBadPasswordRepeatProps'],
      methods: {
        updateIsPublic(data) {
          this.public = data;
        },
        isGoodFormPasswors() {
          this.isBadPassword = false;
          this.$emit('password-updated', this.password);
        },
        isGoodFormPassworsRepeat() {
          this.isBadPassword_repeat = false;
          this.$emit('password-repeat-updated', this.password_repeat);
        },
      },
      data() {
        return {
          password: "",
          password_repeat: "",
        };
      },
    };
  </script>
  
  <style>
    .input-form {
      width: 438px;
      height: 35px;
      border: 1px solid rgb(209, 209, 209);
      border-radius: 11px;
      font-size: 16px;
      padding: 0 0 0 10px;
    }

    .user-information__password {
      margin-top: 12px;
      display: flex;
      padding-left: 25px;
    }
    
    .user-information__password_second {
      margin-left: 12px;
    }
    
    .bad-form {
      border: 1px solid red;
    }

    .good-forms {
      visibility: hidden;
      padding: 0;
      margin: 0;
    }

    .erron-forms {
      visibility: inherit;
      padding: 0;
      margin: 0;
    }
    
  </style>
  