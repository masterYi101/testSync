<template>
  <div>
    <select-tree :tree-data="treeData" v-model="treeValue"> </select-tree>
    <h1>{{ treeValue }}</h1>
  </div>
</template>

<script>
import SelectTree from "@/components/SelectTree";
export default {
  name: "HelloWorld",
  components: { SelectTree },
  data() {
    return {
      treeValue: [ { "name": "三级 2-2-1", "id": "2-2-1" } ],
      treeData: [
        {
          name: "一级 1",
          id: "1",
          children: [
            {
              name: "二级 1-1",
              id: "1-1",
              children: [
                {
                  name: "三级 1-1-1",
                  id: "1-1-1"
                }
              ]
            }
          ]
        },
        {
          name: "一级 2",
          id: "2",
          children: [
            {
              name: "二级 2-1",
              id: "2-1",
              children: [
                {
                  name: "三级 2-1-1",
                  id: "2-1-1"
                }
              ]
            },
            {
              name: "二级 2-2",
              id: "2-2",
              children: [
                {
                  name: "三级 2-2-1",
                  id: "2-2-1"
                }
              ]
            }
          ]
        }
      ],
      tableData: [
        {
          date: "2016-05-02",
          name: "王小虎",
          address:
            "上海市普陀区金沙江路 1518 弄上海市普陀区金沙江路 1518 弄上海市普陀区金沙江路 1518 弄上海市普陀区金沙江路 1518 弄上海市普陀区金沙江路 1518 弄上海市普陀区金沙江路 1518 弄"
        },
        {
          date: "2016-05-04",
          name: "王小虎",
          address: "上海市普陀区金沙江路 1517 弄"
        },
        {
          date: "2016-05-01",
          name: "王小虎",
          address: "上海市普陀区金沙江路 1519 弄"
        },
        {
          date: "2016-05-03",
          name: "王小虎",
          address: "上海市普陀区金沙江路 1516 弄"
        }
      ]
    };
  },
  computed: {},
  watch: {},
  methods: {}
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
