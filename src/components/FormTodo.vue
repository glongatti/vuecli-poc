<template>
  <div class="form-todo form-group">
    <p>
      <input v-model="name" type="text" placeholder="nome" class="form-control" />
    </p>
    <p>
      <textarea v-model="message" type="text" placeholder="message" class="form-control" />
    </p>
    <button v-on:click="addComment" type="submit" class="btn btn-primary">Comentar</button>
  </div>
</template>

<script>
export default {
  data() {
    return {
      name: "",
      message: "",
    };
  },
  methods: {
    addComment() {
      if (this.message.trim() === "") {
        return;
      }

      this.$emit('add-todo',{
        name: this.name,
        message: this.message,
      })

      this.name = "";
      this.message = "";
    },
  },
};
</script>