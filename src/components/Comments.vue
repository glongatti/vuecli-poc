<template>
  <div class="container">
    <h1>Comentários</h1>
    <hr />

    <FormTodo v-on:add-todo="addComment"/>

    <p v-if="comments.length <= 0">Sem comentários</p>

    <div class="list-group">
      <div class="list-group-item" v-for="(comment,index) in allComments" v-bind:key="index">
        <span class="comment_author">
          Author:
          <strong>{{comment.name}}</strong>
        </span>
        <p>{{comment.message}}</p>
        <a v-on:click.prevent="removeComment(index)" href="#" title="Excluir">Excluir</a>
      </div>
    </div>
    <hr />
  </div>
</template>

<script>
import FormTodo from './FormTodo.vue';


export default {
  components:{
    FormTodo
  },
  data() {
    return {
      comments: [],
    };
  },
  methods: {
    addComment(comment){
      this.comments.push(comment);
    },
    removeComment(index) {
      this.comments.splice(index, 1);
    },
  },
  computed: {
    allComments() {
      return this.comments.map((comment) => ({
        ...comment,
        name: comment.name.trim() === "" ? "Anônimo" : comment.name,
      }));
    },
  },
  watch: {
    comments(val) {
      console.log("alterou", val);
    },
  },
};
</script>