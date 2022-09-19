<template>
  <li>
    <span class="comment">{{ comment }}</span>

    <ul class="replies" v-if="replies.length">
      <div v-for="(item, index) in replies" :key="index">
        <recursive-component
          v-bind="{
            comment: item.comment,
            replies: item.replies,
            kitten: item.kitten,
          }"
        />
      </div>
    </ul>
  </li>
</template>

<script>
export default {
  name: "recursive-component",
  props: {
    comment: {
      type: String,
      required: true,
    },
    replies: {
      type: Array,
      default: () => [],
    },
  },
};
</script>