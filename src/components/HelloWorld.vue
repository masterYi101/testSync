<template>
  <div>
    <el-form :model="addForm">
      <el-form-item prop="a">
        <el-select multiple v-model="addForm.a">
          <el-option :value="1" label="杀杀杀杀"></el-option>
          <el-option :value="2" label="杀杀杀杀2222"></el-option>
        </el-select>
      </el-form-item>
      <el-form-item prop="c">
        <el-date-picker v-model="addForm.c"></el-date-picker>
      </el-form-item>
    </el-form>

    <el-button @click="test">
      测试更新按钮
    </el-button>
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
      this.$set(this.addForm, "c", Math.random());
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
