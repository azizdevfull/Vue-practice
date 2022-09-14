<template>
    <navbar class="container" :showModal="showModal" />
    <my-button @click="fetchComments">Get all Comments</my-button>
    <div>
        <my-modal v-model:show="modalVisible"  >
        <comment-form @addComment="createComment" />
        </my-modal>
        <comment-list :comments="comments" @remove="removeComment" />            
    </div>
</template>

<script>
    import CommentForm from './components/CommentForm';
    import CommentList from './components/CommentList';
    import Navbar from '@/components/Navbar';
    import axios from 'axios';
    // import

export default {
    components: {
        CommentForm,
        CommentList,
        Navbar
    },
    data() {
        return {
            comments: [

            ],
            modalVisible: false
        }
    },
    methods: {
        createComment(comment){
            this.comments.push(comment);
            this.modalVisible= false;
        },
        removeComment(comment){
            this.comments = this.comments.filter(c => c.id !== comment.id);

        },
    showModal(){
        this.modalVisible = true;
    },
    async fetchComments(){
        try{
            const response = await axios.get('https://jsonplaceholder.typicode.com/comments?_limit=10');
            this.comments = response.data;
        }catch(e){
            console.log(e);
        }
    }
    },

};
</script>

<style>

</style>
