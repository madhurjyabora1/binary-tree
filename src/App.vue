<template>
  <div class="binary-tree">
    <input v-model="nums" />
    <button @click="createTree">Submit</button>
    <TreeNode :node="treeData" v-if="treeData !== null" />
  </div>
</template>

<script>
import TreeNode from "./components/TreeNode.vue";

export default {
  components: {
    TreeNode,
  },
  data() {
    return {
      nums: "",
      treeData: null,
    };
  },
  methods: {
    createTree() {
      const arr = this.nums.split(",").map((num) => {
        if (num === "null") {
          return null;
        }
        return parseInt(num);
      });
      this.treeData = this.buildTree(arr, 0);
    },
    buildTree(arr, index, parent = null) {
      if (index >= arr.length || arr[index] === null) {
        return null;
      }

      const node = {
        value: arr[index],
        parent: parent,
        left: this.buildTree(arr, 2 * index + 1),
        right: this.buildTree(arr, 2 * index + 2),
      };

      return node;
    },
  },
};
</script>

<style scoped>
.binary-tree {
  display: flex;
  justify-content: center;
  align-items: center;
  height: 100vh;
  flex-direction: column;
}
</style>
