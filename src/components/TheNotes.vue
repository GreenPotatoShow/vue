<template>
    <div class="div">
        <div :key="note.id" v-for="note in notes" class="note">
            <TheNote @delete-note="$emit('delete-note', note.id)" :note="note" />
        </div>
    </div>
</template>

<script>

import TheNote from "./TheNote"
export default {
    name: 'TheNotes',
    props: {
        notes: Array,
        nextNoteId: Number,
        nextNoteTitle: String,
        nextNoteText: String,
    },
    components: {
        TheNote,
    }
}
</script>

<style scoped>
.div{
    display: flex;
    flex-flow: row wrap;
}
.note{
    display: flex;
    flex: 300px;
    margin: 10px;
    background-color: #dbdbdb;
    border: 2px solid #dbdbdb;
    border-radius: 7px;
    max-width: 400px;
}
</style>