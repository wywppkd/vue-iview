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
              title: "leaf 1-1-1",
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
    handleCheckChange(data) {
      console.log(
        "🚀 ~ file: Home.vue ~ line 46 ~ handleCheckChange ~ data",
        data
      );
      const hasLeaf112 = data.find((item) => {
        return item.title === "leaf 1-1-2";
      });

      if (hasLeaf112) {
        const leaf111 = this.data1[0].children[0].children[0];
        this.$set(leaf111, "disableCheckbox", true);
      }

      // const leaf1 = data.find((item) => item.title === "leaf 1-1-1");
      // const leaf2 = data.find((item) => item.title === "leaf 1-1-2");
      // if (leaf1) {
      //   this.$set(
      //     this.data1[0].children[0].children[1],
      //     "disableCheckbox",
      //     true
      //   );
      // }

      // if (leaf2) {
      //   this.$set(
      //     this.data1[0].children[0].children[0],
      //     "disableCheckbox",
      //     true
      //   );
      // }
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
