<template>
  <div class="tree-node">
    <span>{{ node.value }}</span>
    <div class="children" v-if="node && (node.left || node.right)">
      <div class="child-node">
        <TreeNode v-if="node.left" :node="node.left" />
        <TreeNode v-if="node.right" :node="node.right" />
      </div>
    </div>
  </div>
</template>
  
  <script>
export default {
  name: "TreeNode",
  props: {
    node: {
      type: Object,
      default: null,
    },
  },
};
</script>
  
  <style scoped>
.tree-node {
  display: flex;
  flex-direction: column;
  align-items: center;
  padding: 10px;
  margin: 0px;
  min-width: 30px;
}

.children {
  display: flex;
  justify-content: center;
  align-items: center;
}

.child-node {
  display: flex;
  flex-direction: row;
  justify-content: center;
}
</style>
  