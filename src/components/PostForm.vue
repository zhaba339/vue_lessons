<template>
  <form onsubmit="return false">
    <h3>Создание поста</h3>
    <input
      v-model="post.title"
      class="input"
      placeholder="Название"
      type="text"
    />
    <input
      v-model="post.body"
      class="input"
      placeholder="Описание"
      type="text"
    />
    <my-button
        @click="createPost">
        Создать
    </my-button>
  </form>
</template>

<script>
import MyButton from "@/components/UI/MyButton.vue";

export default {
  components: {MyButton},
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
      this.$emit("create", this.post);
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

</style>
