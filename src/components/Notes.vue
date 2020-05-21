<style>
    .hold-note {
        margin: 0 40px;
        display: grid;
        grid-template-rows: 1fr 1fr 1fr;
        grid-template-columns: 1fr 1fr 1fr;
        grid-column-gap: 40px;
        grid-row-gap: 20px;
    }
</style>
<template>
    <section class="hold-note">
    <div v-for="note in notes" :key="note.text">
        <template v-if="!isEditting">
            <Note :getNotes='getNotes' :url='note.url' :text='note.text' :quote='note.quote' :id='note._id' />
        </template>
        <template v-else>
            <h2>Edit me!</h2>
            <input v-model="textEdit" />
             <input v-model="quoteEdit" />
            <button v-on:click="save">Save!</button>
        </template>
    </div>
    </section>
</template>

<script>
import Note from './Note.vue';
export default {
    name: 'Notes',
    components: {
        Note,
    },
    props: {
        notes: Array,
        getNotes: Function,
    },
}
</script>