<style scoped>
    section {
        background: #2a5740;
        border-radius: 20px;
        min-height: 200px;
        color: white;
        padding: 20px;

        display: flex;
        flex-direction: column;
        align-items: space-between;
        justify-content: space-between;
    }
    h1 {
        margin: 0;
    }
    h3 {
        margin: 0;
        color: #FE7762;
        text-shadow: 1px 1px black;
        font-size: 24px;
    }
    h3 span {
        font-size: 18px;
        color: #F5F6FC;
    }

    a {
        color: white;
        font-weight: bold;
        transition: all 0.3s ease-out;
    }
    a:hover {
        color: #FE7762;
    }

    button {
        background: white;
        color: black;
        border-radius: 5px;
        font-weight: bold;
        border: none;
        padding: 5px 10px;
        margin-top: 4px;
    }

    input {
        border-radius: 5px;
        border: none;
        outline: none;
        font-weight: bold;
        font-size: 14px;
        padding: 10px;
        margin: 5px 0;
    }
</style>
<template>
    <section>
        <template v-if="!isEditting">
         <h1>{{text}}</h1>
         <h3><span>&#10075;&#10075;</span> {{quote}} <span>&#10076;&#10076;</span></h3>
         <p><a :href="url" target="_blank">{{url}}</a></p>
         <button v-on:click="edit(quote, url)">Edit</button>
        </template>
        <template v-else>
            <h2>Edit me!</h2>
            <input v-model="quoteEdit" />
             <input v-model="urlEdit" />
            <button v-on:click="save">Save!</button>
        </template>
    </section>
</template>

<script>

export default {
    name: 'Note',
    props: {
        text: String,
        quote: String,
        url: String,
        id: String,
        getNotes: Function,
    },
    data() {
        return {
            isEditting: false,
            urlEdit: '',
            quoteEdit: '',
        }
    },
    methods: {
        save: async function(){
            try {
                await fetch('http://localhost:3000/update/notes', {
                    method: 'POST',
                    credentials: 'same-origin',
                    headers: {
                        'Accept': 'application/json',
                    },
                    body: JSON.stringify({
                        id: this.id,
                        quote: this.quoteEdit,
                        url: this.urlEdit,
                    })
                })
                this.isEditting = false;
                this.getNotes();
            } catch(err) {
                console.log(err);
            }

        },
        edit: function(quote, url) {
            this.isEditting = !this.isEditting;
            this.urlEdit = url;
            this.quoteEdit = quote;
        }
    }
}
</script>