<template>
  <form @submit.prevent="onSubmit">
    <textarea
        v-model="note.value"
        placeholder="Введите значение"
        class="form"
        required
    ></textarea>
    <TagsList :items="tags" @onItemClick="handleTagClick" />
    <button class="btn btnPrimary" type="submit">Создать задачу</button>
  </form>
</template>

<script>
import TagsList from "@/components/UI/TagsList";
export default {
  name: "Form",
  components: { TagsList },
  data() {
    return {
      note: {
        value: "",
        tags: []
      },
      tags: [
        {
          id: 1,
          name: 'home',
          active: false
        },
        {
          id: 2,
          name: 'work',
          active: false
        },
        {
          id: 3,
          name: 'travel',
          active: false
        },
      ],
    }
  },
  methods: {
    onSubmit() {
      this.$emit("onSubmit", this.note)
      this.note.value = ""
      this.note.tags = []
    },
    handleTagClick(tag) {
      if (this.note.tags.length > 0) {
        for (let i = 0; i < this.note.tags.length; i++) {
          if (this.note.tags[i].id === tag.id) {
            this.note.tags.splice(i, 1)
            return
          }
        }
      }
      this.note.tags.push(tag)
      console.log(this.note.tags)

      // this.note.tags.push(tag)
      // console.log(this.note.tags)
    },
  }
}
</script>

<style lang="scss">
.form {
  margin-bottom: 0;
}

</style>