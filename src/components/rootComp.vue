<template>
  <ul class="folders">
    <li>Folders</li>
    <FolderComp :folder="folder" />
  </ul>
</template>

<script>
import FolderComp from "./FolderComp.vue";

export default {
  name: "rootComp",
  props: {
    folder: Object,
  },
  components: {
    FolderComp,
  },
};
</script>

<style scoped>
ul.folders {
  padding: 1rem;
  margin: 0;
  box-sizing: border-box;
  width: 100%;
  list-style: none;
}
ul.folders > li:first-child {
  padding: 1rem 1rem 1rem 0;
}
</style>