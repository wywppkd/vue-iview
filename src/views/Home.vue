<template>
  <div>
    <Tree
      ref="tree"
      :data="data1"
      show-checkbox
      check-strictly
      @on-check-change="handleCheckChange"
    ></Tree>
    <Button @click="handleClick()">按钮</Button>
    <pre>
      {{ data1 }}
    </pre>
  </div>
</template>
<script>
export default {
  name: "Home",
  data() {
    return {
      checkedList: [],
      data1: [
        {
          title: "parent 1",
          expand: true, // 是否展开
          children: [
            {
              title: "leaf 1-1",
              expand: true,
              children: [
                {
                  title: "leaf 1-1-1",
                },
                {
                  title: "leaf 1-1-2",
                },
              ],
            },
          ],
        },
      ],
    };
  },
  mounted() {},
  methods: {
    /** 递归查找指定节点 */
    getNodeNyTitle(data, title) {
      if (!data) {
        return;
      }

      for (const item of data) {
        if (item.title === title) {
          return item;
        }

        // 递归children
        const child = this.getNodeNyTitle(item.children, title);
        if (child) {
          return child;
        }
      }
    },
    handleCheckChange(data) {
      console.log(
        "🚀 ~ file: Home.vue ~ line 46 ~ handleCheckChange ~ data",
        data
      );

      // 从已选节点数组中查看是否有选中"leaf 1-1-2
      const hasLeaf112 = data.find((item) => {
        return item.title === "leaf 1-1-2";
      });
      // 如果有选中: 将"leaf 1-1-1"对应节点设置为禁止勾选状态
      if (hasLeaf112) {
        // 递归查找节点-"leaf 1-1-1"
        const leaf111 = this.getNodeNyTitle(this.data1, "leaf 1-1-1");
        // 将指定节点设置为禁用
        this.$set(leaf111, "disableCheckbox", true);
      }

      // 同上: 如果选择了"leaf 1-1-1"则禁止勾选"leaf 1-1-2"
      const hasLeaf111 = data.find((item) => {
        return item.title === "leaf 1-1-1";
      });
      if (hasLeaf111) {
        const leaf111 = this.getNodeNyTitle(this.data1, "leaf 1-1-2");
        this.$set(leaf111, "disableCheckbox", true);
      }
    },
    handleClick() {
      console.log(
        "🚀 ~ file: Home.vue ~ line 46 ~ mounted ~ this.$refs.tree",
        this.$refs.tree.getCheckedNodes()
      );
    },
  },
};
</script>
