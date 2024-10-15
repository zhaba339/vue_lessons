<template>
  <form onsubmit="return false">
    <h3>Создание поста</h3>
    <my-input
      v-model="post.title"
      placeholder="Название"
      type="text"
    />
    <my-input
      v-model="post.body"
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
import MyInput from "@/components/UI/MyInput.vue";

export default {
  components: {MyInput, MyButton},
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
</style>
