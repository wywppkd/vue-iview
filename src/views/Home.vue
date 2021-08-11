<template>
  <Tree
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
      console.log(
        "🚀 ~ file: Home.vue ~ line 45 ~ handleSelectChange ~ data",
        data
      );
      this.data1[0].disableCheckbox = true;
      this.data1 = [...this.data1];
    },
  },
};
</script>
