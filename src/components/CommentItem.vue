<template>
  <div class="comment">
    <div>
      <p>
        <p> <b>Name: </b>{{ comment.name }}</p>
      </p>
      <p><b>Content:</b> {{ comment.body }} <br>  <b>{{ comment.email }}</b></p>
    </div>
  <div>
    <my-button class="btn btn-danger" @click="$emit('remove', comment)">Delete</my-button>
  </div>
</div>

</template>
<script>
export default {
  props: {
    comment: {
      type: Array,
      required: true,
    },
  },
};
</script>
<style scoped>
    .comment{
        border: 1px solid #ccc;
        padding: 10px;
        margin-bottom: 10px;
        display: flex;
        align-items: center;
        justify-content: space-between;
    }
</style>
