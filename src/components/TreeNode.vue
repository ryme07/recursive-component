<template>
  <div :style="nodeMargin">
    <ul>
      {{
        node.id
      }}
      #{{
        node.label
      }}
      -
      {{
        node.properties
      }}
      <span
        v-if="hasChildren"
        :class="toggleChildrenIcon"
        @click="toggleChildren"
        @keypress="toggleChildren"
      />
    </ul>
    <div v-if="hasChildren">
      <TreeNode
        v-for="child in node.children"
        :key="child.id"
        :node="child"
        :spacing="spacing + 10"
      />
    </div>
  </div>
</template>

<script>
export default {
  name: "TreeNode",
  props: {
    node: {
      type: Object,
      required: true,
    },
    spacing: {
      type: Number,
      default: 0,
    },
  },
  data() {
    return {
      showChildren: false,
    };
  },
  computed: {
    nodeMargin() {
      return {
        "margin-left": `${this.spacing}px`,
      };
    },
    hasChildren() {
      const { children } = this.node;
      return children && children.length > 0;
    },
    toggleChildrenIcon() {
      return this.showChildren ? "fas fa-angle-down" : "fas fa-angle-right";
    },
  },
  methods: {
    toggleChildren() {
      this.showChildren = !this.showChildren;
    },
  },
};
</script>