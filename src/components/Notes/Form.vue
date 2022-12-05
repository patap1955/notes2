<template>
  <form @submit.prevent="onSubmit">
    <textarea
        v-model="note.value"
        placeholder="Введите значение"
        class="form"
        required
    ></textarea>
    <TagsList :items="tags" @onItemClick="handleTagClick" >
      <span>{{  }}</span>
    </TagsList>
    <button class="btn btnPrimary" type="submit">Создать задачу</button>
  </form>
</template>

<script>
import TagsList from "@/components/UI/TagsList";
export default {
  name: "Form",
  components: {TagsList},
  data() {
    return {
      note: {
        value: "",
        tags: []
      },
      val: ["home", "work", "travel"],
      tags: [
        {
          name: 'home',
          active: false
        },
        {
          name: 'work',
          active: false
        },
        {
          name: 'travel',
          active: false
        }
      ]
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
.form {
  margin-bottom: 0;
}

</style>