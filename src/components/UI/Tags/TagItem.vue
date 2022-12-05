<template>
  <span>{{ tag }}</span>
</template>

<script>
export default {
  name: "TagItem",
  props: {
    tag: {
      type: String,
      required: true
    }
  }
}
</script>

<style scoped>

</style>