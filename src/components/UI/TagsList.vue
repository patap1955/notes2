<template>
  <div class="tags-list">
    <div
        class="tag-item"
        v-for="tag in items"
        :key="tag.id"
        @click="$emit('onItemClick', tag)"
        :class="{ isPreview: isPreview, isActive: isActive }"
    >
      <span>{{ tag.name }}</span>
    </div>
  </div>
</template>

<script>
export default {
  name: "TagsList",
  props: {
    items: {
      type: Array,
      required: true
    },
    isPreview: {
      type: Boolean,
      default: false
    },
    isActive: {
      type: Boolean,
      default: false
    }
  },
  methods: {
    onTagClick() {
      console.log(123)
    }
  }
}
</script>

<style lang="scss">
  .tags-list {
    padding: 10px 0;
    display: flex;
    justify-content: center;
  }
  .tag-item {
    padding: 8px 22px;
    margin-right: 10px;
    background-color: #fff;
    border-radius: 22px;
    user-select: none;
    cursor: pointer;
    &.isActive {
      background-color: #444ce0;
      color: #fff;
    }
    &.isPreview {
      padding: 0;
      color: #444ce0;
      cursor: default;
      &:before {
        content: '#';
      }
    }
    &:last-child {
      margin-right: 0;
    }
  }
</style>