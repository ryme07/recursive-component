<template>
  <div>
    <ul v-for="(item, index) in comments" :key="index" class="comments">
      <RecursiveComponent
        v-bind="{
          comment: item.comment,
          replies: item.replies,
          kitten: item.kitten,
        }"
      />
    </ul>

    <TreeNode v-for="node in nodes" :key="node.id" :node="node" />

    <RootComp v-bind:folder="root" />
  </div>
</template>

<script>
import RecursiveComponent from "./components/RecursiveComponent.vue";
import TreeNode from "@/components/TreeNode";
import RootComp from "./components/rootComp.vue";

export default {
  name: "App",
  components: {
    RecursiveComponent,
    TreeNode,
    RootComp,
  },
  data() {
    return {
      comments: [
        {
          comment: "First comment",
          replies: [
            {
              comment: "sub-comment 1 for comment 1",
              replies: [
                {
                  comment: "sub-sub-comment 1",
                  replies: [
                    {
                      comment: "sub-sub-sub-comment 1 replies",
                      replies: [
                        {
                          comment: "label 1",
                        },
                        {
                          comment: "input 1",
                        },
                      ],
                    },
                    { comment: "sub-sub-sub-comment 2 replies" },
                  ],
                },
                { comment: "sub-sub-comment 2" },
              ],
            },
            { comment: "sub-comment 2 for comment 1" },
          ],
        },

        {
          comment: "Second comment",
          replies: [
            {
              comment: "sub-comment 1 for comment 2 comment replies",
              replies: [
                {
                  comment: "sub-sub-comment 1 replies",
                  kitten: [
                    {
                      label: "label 1",
                    },
                    {
                      input: "input 1",
                    },
                  ],
                },
                { comment: "sub-sub-comment 2 replies" },
              ],
            },
            { comment: "sub-comment 2 for comment 2 comment replies" },
          ],
        },
      ],

      root: {
        text: "Root Folder",
        leaf: false,
        expanded: true,
        children: [
          {
            text: "Sub Folder 1",
            leaf: false,
            expanded: false,
            children: [
              {
                text: "Sub Sub Folder 1",
                leaf: false,
                expanded: false,
                children: [
                  {
                    label: "lavel",
                    properties: [
                      {
                        name: "name",
                      },
                    ],
                    text: "SomeFile1.js",
                    leaf: true,
                  },
                ],
              },
              {
                text: "Sub Sub Folder 2",
                leaf: false,
                expanded: false,
                children: [
                  {
                    label: "lave",
                    properties: [
                      {
                        name: "name 2",
                      },
                    ],

                    leaf: true,
                  },
                ],
              },
              {
                text: "SomeFile.txt",
                leaf: true,
              },
            ],
          },
        ],
      },
    };
  },

  computed: {
    nodes() {
      return [
        {
          id: 1,
          label: "Foods",
          children: [
            {
              id: 2,
              label: "Fruits",
              properties: [{ name: "prop name 1" }],
              children: [
                {
                  id: 3,
                  label: "Banana",
                  properties: [{ name: "prop name 2" }],
                },
                {
                  id: 4,
                  label: "Apple",
                  properties: [{ name: "prop name 3" }],
                },
                {
                  id: 5,
                  label: "Strawberry",
                  properties: [{ name: "prop name 4" }],
                },
              ],
            },
            {
              id: 6,
              label: "Vegetables",
              children: [
                {
                  id: 7,
                  label: "Carrot",
                },
                {
                  id: 8,
                  label: "Lettuce",
                },
                {
                  id: 9,
                  label: "Potato",
                },
              ],
            },
          ],
        },
        {
          id: 10,
          label: "Drinks",
          children: [
            {
              id: 11,
              label: "Beers",
              children: [
                {
                  id: 12,
                  label: "Budweiser",
                },
                {
                  id: 13,
                  label: "Heineken",
                },
              ],
            },
            {
              id: 14,
              label: "Wines",
            },
            {
              id: 15,
              label: "Whiskey",
            },
          ],
        },
      ];
    },
  },
};
</script>

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;

  color: #2c3e50;
  margin-top: 60px;
}
ul {
  list-style: none;
}
</style>
