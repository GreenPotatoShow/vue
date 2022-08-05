<template>
  <div class="container">
    <TheHeader @btn-click="showAddNote" title="Заметки" :showAdd="showAdd"/>
    <div v-show="showAdd">
          <AddNote @add-note="addNote"/>
    </div>
    <TheNotes @delete-note="deleteNote" :notes="notes" />
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

import AddNote from './components/AddNote'
import TheHeader from './components/TheHeader'
import TheNotes from './components/TheNotes'
export default {
  name: 'App',
  components: {
    TheHeader,
    TheNotes,
    AddNote
  },
  data() {
    return{
      notes: [],
      showAdd: false,
    }
  },
  created() {
    this.notes = [
      {
        id: 0,
        title: 'Title',
        date: formatDate(new Date()),
        text: 'Text',
      },
      {
        id: 1,
        title: 'Заметка',
        date: formatDate(new Date()),
        text: 'Lorem ipsum dolor sit amet consectetur adipisicing elit. Tenetur asperiores libero nobis perferendis vel. Quibusdam natus consectetur magni beatae architecto sequi nesciunt explicabo esse? Consequuntur aspernatur ipsum atque similique fugiat.',
      },
      {
        id: 2,
        title: 'Заметка',
        date: formatDate(new Date()),
        text: 'Lorem ipsum dolor sit amet consectetur adipisicing elit. Tenetur asperiores libero nobis perferendis vel. Quibusdam natus consectetur magni beatae architecto sequi nesciunt explicabo esse? Consequuntur aspernatur ipsum atque similique fugiat.',
      }
      ];
  },
  methods: {
    showAddNote(){
      this.showAdd = !this.showAdd;
    },
    deleteNote(id){
      if (confirm('Удалить заметку?')){
        this.notes = this.notes.filter((note) => note.id !== id)
      }
    },
    addNote(note){
      this.notes = [...this.notes, note];
    }
  }
}
</script>

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  color: #2c3e50;
  margin: 30px 40px;
}
</style>
