<template>
  <div v-bind:class="[this.isGoodReg ? 'bad' : '', 'content']">

    <h3 class="content__title">Регистрация</h3>

    <div class="user-information">
      <Username
        @name-updated="updateIsName"
        @email-updated="updateIsEmail"
        :isBadNameProps="isBadName"
        :isBadEmailProps="isBadEmail"
      />
        
      <SelectVue
        @select-updated="updateIsSelect" :isBadRoleProps="isBadRole"
      />
      <Password
        @password-updated="updateIsPassword"
        @password-repeat-updated="updateIsPasswordRepeat"
        :isBadPasswordProps="isBadPassword"
        :isBadPasswordRepeatProps="isBadPassword_repeat"
      />

    </div>

    <div class="accept-rules">

      <div class="accept-rules__public-profile">

        <Switcher @public-updated="updateIsPublic"/>
        <AcceptRules />

      </div>

      <div class="registration">

        <input
          type="checkbox"
          id="checkbox"
          v-model="isChecked"
          v-bind:class="[this.isBadChecked ? 'bad-form' : '', 'registration-checkbox']"
          v-on:change="isGoodFormCheck">
        <label for="checkbox"></label>

        <RegistrationText />

        <button class="registration__button" v-on:click="register">Зарегестрироваться</button>

      </div>

      <p v-bind:class="[this.isChecked ? 'good-forms-check' : 'error-forms-check']">без этого пунка регистрация не возможна</p>

    </div>

  </div>

  <div v-bind:class="[this.isGoodReg ? 'good' : '', 'successfulRegistration']"><h2>Регистрация успешно завершена</h2></div>
</template>

<script>
  import Switcher from './components/Switcher.vue'
  import Password from './components/Password.vue';
  import SelectVue from './components/SelectVue.vue';
  import Username from './components/Username.vue';
  import AcceptRules from './components/AcceptRules.vue'
  import RegistrationText from './components/RegistrationText.vue'

  export default {
    name: 'App',
    methods: {
      showContent(elementRef) {
        const content = this.$refs[elementRef].value;
        console.log(content);
      },
      updateIsPublic(data) {
        this.public = data;
      },
      updateIsName(data) {
        this.isBadName = false;
        this.username = data;
      },
      updateIsEmail(data) {
        this.isBadEmail = false;
        this.email = data;
      },
      updateIsSelect(data) {
        this.isBadRole = false;
        this.role = data;
      },
      updateIsPassword(data) {
        this.isBadPassword = false;
        this.password = data;
      },
      updateIsPasswordRepeat(data) {
        this.isBadPassword_repeat = false;
        this.password_repeat = data;
      },
      register(){
        if(!this.isChecked) {this.isBadChecked = true}
        if(!this.username) this.isBadName = true
        if(!this.role) this.isBadRole = true
        if(!this.email) this.isBadEmail = true
        if(!this.password) this.isBadPassword = true
        if(!this.password_repeat) this.isBadPassword_repeat = true
        if(this.isBadChecked || this.isBadName || this.isBadRole || this.isBadEmail || this.isBadPassword || this.isBadPassword_repeat) return
        if(this.password !== this.password_repeat) {
          this.isBadPassword_repeat = true;
          return;
        }
        console.log(this.isChecked, this.username, this.role, this.email, this.password, this.password_repeat);
        this.isGoodReg = true;
      },
      isGoodFormPasswors() {
        this.isBadPassword = false;
      },
      isGoodFormPassworsRepeat() {
        this.isBadPassword_repeat = false;
      },
      isGoodFormName() {
        this.isBadName = false;
      },
      isGoodFormEmail() {
        this.isBadEmail = false;
      },
      isGoodFormRole() {
        this.isBadRole = false;
      },
      isGoodFormCheck() {
        this.isBadChecked = false;
      },
    },
    components: {
      Switcher, Password, SelectVue, Username, AcceptRules, RegistrationText
    },
    data() {
      return {
        isChecked: true,
        public: false,
        username: "",
        role: "",
        email: "",
        password: "",
        password_repeat: "",

        isBadName: false,
        isBadEmail: false,
        isBadRole: false,
        isBadPassword: false,
        isBadPassword_repeat: false,
        isBadChecked: false,

        isGoodReg: false,
      };
    },
  };
</script>

<style>
body {
  margin: 0;
  padding: 0;
}

#app {
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  margin: 0;
  padding: 0;
  width: 100%;
  min-height: 100vh;
  display: flex;
  align-items: center;
  justify-content: center;
  font-family: 'Montserrat', sans-serif;
}

.content {
  width: 960px;
  height: 547px;
  border-radius: 15px;
  border:  1px solid rgb(209, 209, 209);
  margin-bottom: 200px;
}

.content__title {
  margin: 22px 0 25px 31px;
  padding: 0 ;
  display: flex;
  font-size: 27px;
}

.user-information {
  display: flex;
  flex-direction: column;
  justify-content: left;
  border-top: 1px solid rgb(209, 209, 209);
  border-bottom: 1px solid rgb(209, 209, 209);
  padding-bottom: 30px;
}


.accept-rules__public-profile {
  display: flex;
  flex-direction: row;
}


.registration {
  display: flex;
  flex-direction: row;
  margin-top: 15px;
}

.registration__button {
  width: 300px;
  height: 40px;
  border-radius: 8px;
  background-color: #c9dbff;
  color: #497ADA;
  border: 0;
  font-size: 14px;
  margin-left: 20px;
}

#checkbox {
  width: 19px;
  height: 17px;
  border-radius: 5px;
  background-color: #3586FF;
  margin: 0 0 0 27px;
}

.bad-form {
  border: 1px solid red;
  border-color: red;
}

.successfulRegistration {
  width: 500px;
  height: 300px;
  border: 1px solid rgb(209, 209, 209);
  border-radius: 30px;
  display: none;
  padding-top: 100px;
}

.good {
  display: block;
}

.bad {
  display: none;
}

.good-forms-check {
  padding: 0;
  margin: 0;
  visibility: hidden;
}

.error-forms-check {
  text-align: left;
  color: rgb(185, 2, 2);
  padding: 0;
  margin: 0;
  margin-left: 15px;
}

</style>
