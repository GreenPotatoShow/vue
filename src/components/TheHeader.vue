<template>
    <header>
        <h1>{{title}}</h1>
        <TheButton @btn-click="$emit('btn-click')" :text="showAdd ? 'Скрыть' : 'Добавить заметку'"/>
    </header>
</template>


<script>
import TheButton from './TheButton.vue'
export default {
    name: 'TheHeader',
    props: ['title', 'showAdd'],
    components: {
        TheButton,
    }
}
</script>

<style scoped>
    header{
        display: flex;
        flex-wrap: wrap;
        align-items: center;
        justify-content: space-between;
        margin-bottom: 20px;
    }
    h1{
        font-size: 50pt;
        margin-top: 0;
        margin-left: 10px;
        flex: 300px;
    }
</style>