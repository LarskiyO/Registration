<template>
    <div class="registration__text">
        Регистрируясь, Вы соглашаетесь  с
        <span class="registration__text-blue">политикой конфиденциальности</span>
        <br>
        и обработкой
        <span class="registration__text-blue">персональных данных</span>
    </div>
</template>
<script>
    export default {
        name: 'RegistrationText',
    };
</script>
<style>
    .registration__text {
    text-align: left;
    margin-left: 12px;
    font-size: 16px;
    }

    .registration__text-blue {
    width: 100%;
    color: #3586FF;
    }
    
</style>
    