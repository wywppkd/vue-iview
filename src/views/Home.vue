<template>
  <Tree
    :data="data1"
    show-checkbox
    check-strictly
    @on-select-change="handleSelectChange"
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
    handleSelectChange(data) {
      console.log(
        "🚀 ~ file: Home.vue ~ line 45 ~ handleSelectChange ~ data",
        data
      );
    },
  },
};
</script>
