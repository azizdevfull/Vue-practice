<template>
    <navbar class="container" :showModal="showModal" />
    <div>
        <my-modal v-model:show="modalVisible"  >
        <comment-form @addComment="createComment" />
        </my-modal>
        <comment-list :comments="comments" @remove="removeComment" v-if="!isLoading" />  
                <div v-else class="spinner-grow col-md-3 offset-md-6" role="status">
                    <span class="visually-hidden m-auto">Loading...</span>
                </div>
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
            comments: [],
            modalVisible: false,
            isLoading: false,
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
            this.isLoading = true;
            const response = await axios.get('https://jsonplaceholder.typicode.com/comments?_limit=10');
            this.comments = response.data;
        }catch(e){
            alert('Something went wrong')
        }finally{
            this.isLoading = false;
        }
    }
    },
    mounted(){
        this.fetchComments();
    }

};
</script>

<style>

</style>
