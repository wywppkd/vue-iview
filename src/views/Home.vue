<template>
  <Tree
    ref="tree"
    :data="data1"
    show-checkbox
    check-strictly
    @on-check-change="handleCheckChange"
  ></Tree>
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
              title: "parent 1-1",
              expand: true,
              checked: true,
              children: [
                {
                  title: "leaf 1-1-1",
                },
                {
                  title: "leaf 1-1-2",
                },
              ],
            },
            {
              title: "parent 1-2",
              expand: true,
              children: [
                {
                  title: "leaf 1-2-1",
                },
                {
                  title: "leaf 1-2-1",
                },
              ],
            },
          ],
        },
      ],
    };
  },
  methods: {
    handleCheckChange(data) {
      this.$nextTick(() => {
        this.data1[0].disableCheckbox = true;
        console.log(
          "🚀 ~ file: Home.vue ~ line 59 ~ this.$nextTick ~ this.data1",
          this.data1
        );
      });
    },
  },
};
</script>
