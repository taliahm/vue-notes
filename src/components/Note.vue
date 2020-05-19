<template>
    <section>
    <div v-for="note in notes" :key="note.text">
        <template v-if="!isEditting">
         <p>{{note.text}}</p>
         <p>{{note.quote}}</p>
         <a :href="note.url" target="_blank">{{note.url}}</a>
         <button v-on:click="edit(note.text, note.quote)">Edit this!</button>
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
export default {
    name: 'Note',
    props: {
        notes: Array,
    },
    data() {
        return {
            isEditting: false,
            textEdit: '',
            quoteEdit: '',
        }
    },
    methods: {
        save: function() {
            console.log('save!');
        },
        edit: function(text, quote) {
            this.isEditting = !this.isEditting;
            this.textEdit = text;
            this.quoteEdit = quote;
        }
    }
}
</script>