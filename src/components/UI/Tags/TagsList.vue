<template>
  <div class="tags-list">
    <div
        class="tag-item"
        v-for="tag in items"
        :key="tag"
        @click="setActive(tag)"
        :class="{ isPreview: isPreview, isActive: isActive }"
    >
      <TagItem :tag="tag" />
    </div>
  </div>
</template>

<script>
import TagItem from "@/components/UI/Tags/TagItem";
export default {
  name: "TagsList",
  components: {TagItem},
  data() {
    return {
      tags: []
    }
  },
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
  created() {
    this.tags = this.items
  },
  methods: {
    setActive(tag) {
      const isActive = true
      console.log(this.tags)
      this.$emit('onItemClick', tag)
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