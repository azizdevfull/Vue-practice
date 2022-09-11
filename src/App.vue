<template>
    <div>
        <comment-form @addComment="createComment" />
        <comment-list :comments="comments" />
    </div>
</template>

<script>
    import CommentForm from './components/CommentForm';
    import CommentList from './components/CommentList';

export default {
    components: {
        CommentForm,
        CommentList,
    },
    data() {
        return {
            comments: [
                { id: 1, name: "Aziz", email: "aziz@gmail.com", content: "Lorem ipsum dolor sit" },
                { id: 2, name: "Murod", email: "murod@gmail.com", content: "Lorem ipsum dolor sit" },
                { id: 3, name: "Aziza", email: "aziza@gmail.com", content: "Lorem ipsum dolor sit" },


            ],
        }
    },
    methods: {
        createComment(comment){
            this.comments.push(comment);
        }
    },
};
</script>

<style>

</style>
