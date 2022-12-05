<template>
  <form @submit.prevent="onSubmit">
    <textarea
        v-model="note.value"
        placeholder="Введите значение"
        required
    ></textarea>
    <TagsList :items="tags" @onItemClick="handleTagClick" />
    <button class="btn btnPrimary" type="submit">Создать задачу</button>
  </form>
</template>

<script>
import TagsList from "@/components/UI/Tags/TagsList";
export default {
  name: "Form",
  components: {TagsList},
  data() {
    return {
      note: {
        value: "",
        tags: []
      },
      tags: ["home", "work", "travel"],
    }
  },
  methods: {
    onSubmit() {
      this.$emit("onSubmit", this.note)
      this.note.value = ""
    },
    handleTagClick(tag) {
      this.note.tags.push(tag)
      console.log(this.note)
    }
  }
}
</script>

<style lang="scss">
  textarea {
    margin-bottom: 0;
  }
</style>