<template>
    <div>
        <div class="w-75 mx-auto">
            <h3>Add Comment</h3>
            <form @submit.prevent>
                <input v-model="comment.name" placeholder="Name"
                    class="form-control" />
                <input v-model="comment.email" placeholder="Email"
                    class="form-control my-3" />
                <input v-model="comment.content" placeholder="Content"
                    class="form-control" />
                <div style="text-align: right;">
                    <button @click="createComment" class="btn btn-primary mt-3 ml-auto a">Add Comments</button>
                </div>
            </form>
        </div>
    </div>
</template>

<script>
export default {
    data() {
        return {
            comment: {
            name: "",
            email: "",
            content: ""
            }
        }
    },
    methods: {
        createComment(){
            this.comment.id = Date.now();
            this.$emit('addComment', this.comment);
            this.comment = {
                name: "",
                email: "",
                content: ""
            }
        }
    }
}
</script>

<style>
    
</style>