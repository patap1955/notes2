<template>
  <Form @onSubmit="handleSubmit" />
  <List @onRemove="handleRemove" :items="notes" />
</template>

<script>
import Form from "@/components/Notes/Form";
import List from "@/components/Notes/List";
export default {
  name: "Home",
  components: {List, Form},
  data() {
    return {
      notes: [
        {
          id: 1,
          title: 'task1',
          tags: [
            {
              id: 1,
              name: 'home',
              active: true
            },
            {
              id: 2,
              name: 'work',
              active: true
            },
          ],
          edit: true
        },
        {
          id: 2,
          title: 'task2',
          tags: [
            {
              id: 3,
              name: 'travel',
              active: true
            }
          ],
          edit: true
        },
        {
          id: 3,
          title: 'task3',
          tags: [],
          edit: true
        },
      ]
    }
  },
  mounted() {
    this.getNotes();
  },
  watch: {
    notes: {
      handler(updatedList) {
        localStorage.setItem('notes', JSON.stringify(updatedList))
      },
      deep: true
    }
  },
  methods: {
    handleSubmit(array) {
      
      let id = 1
      if (this.notes.length > 0) {
        const lastNotes = this.notes.at(-1)
        id = lastNotes.id + 1
      }
      const note = {
        id: id,
        title: array.value,
        tags:   array.tags,
        edit: true
      }
      console.log(note)
      this.notes.push(note);
    },
    handleRemove(id) {
      const index = this.noteIndex(id)
      this.notes.splice(index, 1)
    },
    noteIndex(id) {
      return this.notes.findIndex(item => item.id === Number(id))
    },
    getNotes() {
      const localNotes = localStorage.getItem("notes");
      if (localNotes) {
        this.notes = JSON.parse(localNotes);
      }
    }
  }
}
</script>

<style scoped>

</style>