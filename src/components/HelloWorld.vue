<template>
  <div>
    <el-popconfirm @confirm="test">
      <el-button slot="reference">
        测试更新按钮
      </el-button>
    </el-popconfirm>
  </div>
</template>

<script>
export default {
  name: "HelloWorld",
  data() {
    return {
      addForm: {
        a: [1],
        c: null,
        d: 2
      }
    };
  },
  // mounted() {
  //   this.$watch(
  //     "addForm.a",
  //     function() {
  //       console.log("a");
  //     },
  //     { immediate: true }
  //   );
  //   this.$watch(
  //     "addForm.c",
  //     function() {
  //       console.log("c");
  //     },
  //     { immediate: true }
  //   );
  // },
  computed: {},
  watch: {
    "addForm.a": {
      handler(newVal) {
        console.log("aa", newVal);
      },
      immediate: true
    },
    "addForm.d": {
      handler() {
        console.log("ddd");
      },
      immediate: true
    },
    "addForm.c": {
      handler() {
        console.log("ccc");
      },
      immediate: true
    }
  },
  methods: {
    test() {
     debugger
    }
  }
};
</script>

<style scoped lang="scss">
.drag {
  width: 200px;
  resize: both;
  position: relative;
  &::after {
    display: block;
    content: "";
    width: 100%;
    height: 100%;
    position: absolute;
    left: 0;
    top: 0;
    border: 1px solid red;
  }
}
</style>
