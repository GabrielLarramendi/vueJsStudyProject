<template>
    <div class="container">
    <h1>Comentarios</h1>
        <hr />
        <FormComment v-on:add-comment="addComment"></FormComment>
        <hr />
        <div class="list-group">
            <p v-if="comments.length <= 0">Sem comentarios</p>
            <div v-else class="list-group-item" v-for="(comment, index) in allComments" :key="index">
                <span class="comment_author">Autor: <strong> {{ comment.name }}</strong></span>
                <p> {{ comment.message }}</p>
                <div>
                    <a href="#" title="Excluir" v-on:click.prevent="removeComment(index)">Excluir</a>
                </div>
            </div>
        </div>
    </div>
</template>

<script>
    import FormComment from './FormComment.vue';
    export default {
        components: {
            FormComment
        },

        data() {
            return {
                comments: [],
            }
        }, 
        methods: {
            
            addComment(comment) {
                this.comments.push(comment)
            },

            removeComment(index) {
                this.comments.splice(index, 1);
            }
        },

        computed: {
            allComments() {
                return this.comments.map(comment => ({
                    ...comment,
                    name: comment.name.trim() === '' ? 'Anonimo' : comment.name
                }))
            }
        },
        
        watch: {
            comments(val) {
                console.log('val', val)
            }
        }
    }
    
</script>

