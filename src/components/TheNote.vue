<template>
    <div class="note">
        <div class="title">
            <h3>{{note.title}}</h3>
            <div @click="onDelete(note.id)"  class="remove">x</div>
        </div>
        <p class="date">{{note.date}}</p>
        <div class="text">{{note.text}}</div>
    </div>
    
</template>

<script>
export default {
    name: "TheNote",
    props: {
        note: Object
    },
    methods: {
        onDelete(id){
            this.$emit('delete-note', id);
        }
    }
}
</script>

<style scoped>
    .note{
        display: flex;
        flex-flow: column wrap;
        flex: 300px;
    }
    .date{
        margin-top: 0;
        margin-left: 5px;
        font-size: 10pt;
        font-weight: bold;
    }
    .title{
        display: flex;
        flex-flow: row nowrap;
        justify-content: space-between;
    }
    h3{
        display: flex;
        font-size: 30pt;
        margin-bottom: 0;
        margin-top: 0;
    }
    .remove{
        display: flex;
        font-family: Avantgarde, TeX Gyre Adventor, URW Gothic L, sans-serif;
        margin-top: -5px;
        cursor: pointer;
    }
    .remove:hover{
        color: grey;
    }
    .text{
        margin-top: -5px;
        font-family: Arial Narrow, sans-serif;
        font-size: 15pt;
    }
</style>