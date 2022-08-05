<template>
<div class="div">
    <form @submit="onSubmit" class="add-form">
        <div class="title">
            <label>Заголовок</label>
            <input type="text" v-model="title" name="title" placeholder="Title" autocomplete = "off" />
        </div>
        <div class="text">
            <label>Заметка</label>
            <textarea v-model="text" name="text" placeholder="Text" autocomplete = "off"> </textarea>
        </div>
        <input type="submit" value="Сохранить" class="btn"/>
    </form>
</div>
</template>

<script>
const formatDate = (date) => {
    let dd =  date.getDate();
    if (dd < 10){
        dd = '0' + dd;
    }
    let mm =  date.getMonth();
    if (mm < 10){
        mm = '0' + mm;
    }
    return dd + '.' + mm + '.' +  date.getFullYear();
}
    export default {
        name: 'AddNote',
        data(){
            return {
                title: '',
                date: formatDate(new Date()),
                text: ''
            }
        },
        methods: {
            onSubmit(e){
                e.preventDefault();
                if (!this.title&&!this.text){
                    alert('Нельзя создать пустую заметку!');
                    return;
                }
                const newNote = {
                    id: Math.floor(Math.random()* 100000),
                    title: this.title,
                    date: formatDate(new Date()),
                    text: this.text,
                }
                this.$emit('add-note', newNote);
                this.text = '';
                this.title = '';
            }
        }
    }
</script>

<style scoped>
    .div{
        display: flex;
        flex-direction: row;
        justify-content: flex-end;
    }
    .add-form{
        display: flex;
        flex-flow: column nowrap;
        min-width: 30%;
        max-width: 50%;
        margin-top: -50px;
        background-color: #ebebeb;
        border: 2px solid #ebebeb;
        border-radius: 7px;
        padding: 20px;
        font-weight: bold;
        justify-content: space-between;
    }
    .title{
        display: flex;
        flex-flow: row wrap;
        align-items: center;
        justify-content: space-between;
    }
    .title>input{
        display: flex;
        margin-left: 10px;
        margin-bottom: 5px;
        border: 2px solid grey;
        border-radius: 5px;
        font-family: Arial Narrow, sans-serif;
        font-size: 15pt;
        width: 70%;
    }
    label{
        display: flex;
    }
    .text{
        display: flex;
        flex-flow: row wrap;
        align-items: center;
        justify-content: space-between;
    }
    textarea{
        margin-left: 10px;
        border: 2px solid grey;
        border-radius: 5px;
        font-family: Arial Narrow, sans-serif;
        font-size: 15pt;
        width: 75%; 
    }
    .btn {
        margin-top: 10px;
        padding: 15px 20px;
        background-color: black;
        color: white;
        border: 2px solid black;
        border-radius: 5px;
        font-size: 15pt;
        cursor: pointer;
    }
    .btn:hover {
        background-color: #535353;
        border: 2px solid #535353;
    }
    .btn:active {
        background-color: #797979;
        border: 2px solid #797979;
    }
</style>