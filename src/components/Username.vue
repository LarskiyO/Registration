<template>

    <h3 class="user-information__title">Заполните Ваши данные</h3>

    <div class="user-information__name-email">

        <div>
            <input
                placeholder="Имя"
                v-bind:class="[this.isBadNameProps ? 'bad-form' : '', 'user-information__name-email_input-name input-form']"
                v-model="username"
                v-on:change="isGoodFormName"
            />
            <p
                v-bind:class="[this.isBadNameProps ? 'erron-forms-username' : 'good-forms-username']">
                введите имя
            </p>
        </div>


        <div>
            <input
                placeholder="Email"
                v-bind:class="[this.isBadEmailProps ? 'bad-form' : '', 'user-information__name-email_input-email input-form']"
                v-bind:id="[this.isValidateEmail ? 'bad-form' : '']"
                v-model="email"
                v-on:change="isGoodFormEmail"
            />
            <p v-bind:class="[this.isBadEmailProps ? 'erron-forms-username' : 'good-forms-username']">email введен не правилно</p>
        </div>

    </div>

</template>

<script>

    export default {
        name: 'Username',
        emits: ['name-updated', 'email-updated'],
        props: ['isBadNameProps', 'isBadEmailProps'],
        methods: {
            isGoodFormName() {
                this.isBadName = false;
                this.$emit('name-updated', this.username);
            },
            isGoodFormEmail() {
                const regex = /^[A-Za-z0-9]+$/;
                if (!regex.test(this.email)) {
                    this.isValidateEmail = false;
                } else {
                    this.isValidateEmail = true;
                }
                this.isBadEmail = false;
                this.$emit('email-updated', this.email);
            },
        },

        data() {
            return {
                username: "",
                email: "",
                isValidateEmail: false,
            };
        },
    };
</script>
  
<style>

    .user-information__title {
        font-size: 16px;
        font-weight: 500;
        width: 212px;
        margin: 20px 0 0 27px;
    }


    .user-information__name-email {
        display: flex;
        margin-top: 30px;
    }

    .input-form {
        width: 438px;
        height: 35px;
        border: 1px solid rgb(209, 209, 209);
        border-radius: 11px;
        font-size: 16px;
        padding: 0 0 0 10px;
    }

    .user-information__name-email_input-name {
        margin-left: 26px;
    }

    .user-information__name-email_input-email {
        margin-left: 12px;
    }

    .bad-form {
        border: 1px solid red;
    }

    #bad-form {
        border: 1px solid red;
    }

    .good-forms-username {
      visibility: hidden;
      padding: 0;
      margin: 0;
    }

    .erron-forms-username {
      visibility: inherit;
      padding: 0;
      margin: 0;
    }

</style>
  