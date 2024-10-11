<template>
  <form onsubmit="return false">
    <h4>Создание поста</h4>
    <input
      v-model="post.title"
      class="input"
      placeholder="Название"
      type="text"
      @input="post.title = $event.target.value"
    />
    <input
      v-model="post.body"
      class="input"
      placeholder="Описание"
      type="text"
      @input="post.body = $event.target.value"
    />
    <button class="btn" @click="createPost">Создать</button>
  </form>
</template>

<script>
export default {
  data() {
    return {
      post: {
        title: "",
        body: "",
      },
    };
  },

  methods: {
    createPost() {
      this.post.id = Date.now();
      this.$emit("create", this.post, "fdsf", "fdsfsdfdsf");
      this.post = {
        title: "",
        body: "",
      };
    },
  },
};
</script>

<style scoped>
form {
  display: flex;
  flex-direction: column;
}

.input {
  width: 100%;
  border: 1px solid teal;
  padding: 10px 15px;
  margin-top: 15px;
}

.btn {
  margin-top: 15px;
  align-self: flex-end;
  padding: 10px 15px;
  background: none;
  color: teal;
  border: 1px solid teal;
}
</style>
