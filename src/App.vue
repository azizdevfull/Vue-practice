<template>
    <navbar class="container" :showModal="showModal" />
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
                { id: 1, name: "Aziz", email: "aziz@gmail.com", content: "Lorem ipsum dolor sit" },
                { id: 2, name: "Murod", email: "murod@gmail.com", content: "Lorem ipsum dolor sit" },
                { id: 3, name: "Aziza", email: "aziza@gmail.com", content: "Lorem ipsum dolor sit" },
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
    }
    },

};
</script>

<style>

</style>
