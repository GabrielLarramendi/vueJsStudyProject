<template>
    <div class="form-comments form-group">
        <p>
            <input placeholder="Nome" type="text" name="author" class="form-control" v-model="name"/>
        </p>
        <p>
            <textarea placeholder=" Comentário" name="message" v-model="message"></textarea>
        </p>
        <button v-on:click="addComment" type="submit" class="btn btn-primary">Comentar</button>
    </div>
</template>

<script>
    export default {
        data() {
            return {
                name: '',
                message: ''
            }
        },
        methods: {
            addComment() {
                if (this.message.trim() === '') {
                    console.log("Os dois campos sao obrigatorios!");
                    return;
                }

                this.$emit('add-comment', {
                    name: this.name,
                    message: this.message
                })

                        
                this.name = '';
                this.message = '';
            },
        }
    }
</script>