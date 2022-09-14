<template>
    <div>
        <div class="w-75 mx-auto">
            <h3>Add Comment</h3>
            <form @submit.prevent>
                <my-input v-model="comment.name" placeholder="Name"
                    class="form-control" />
                <my-input v-model="comment.email" placeholder="Email"
                    class="form-control my-3" />
                <my-input v-model="comment.body" placeholder="Content"
                    class="form-control" />
                <div style="text-align: right;">
                    <my-button @click="createComment" class="btn btn-primary mt-3 ml-auto a">Add Comments</my-button>
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
            body: ""
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
                body: ""
            }
        }
    }
}
</script>

<style>
    
</style>