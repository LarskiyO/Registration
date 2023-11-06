<template>
    <div class="accept-rules__title-wrap">

        <h3 class="accept-rules__title-wrap_title">Хотите чтобы Ваш профиль видели другие участники платформы?</h3>
        <span class="accept-rules__title-wrap_text">Включает профиль для просмотра другими пользователями по ссылке</span>

    </div>
</template>
<script>
    export default {
        name: 'AcceptRules',
    };
</script>
<style>
    .accept-rules__title-wrap {
        margin: 21px 0 0 0;
        display: flex;
        flex-direction: column;
        justify-content: left;
    }

    .accept-rules__title-wrap_title {
        margin: 0 0 0 7px;
        padding: 0;
        font-size: 18px;
    }

    .accept-rules__title-wrap_text {
        margin: 16px 0 0 6px;
        padding: 0;
        width: 600px;
        font-size: 16px;
        color: gray;
    }
    
</style>
    