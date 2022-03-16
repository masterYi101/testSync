<template>
  <el-popover
    popper-class="select-tree-pop"
    :width="popWidth"
    :placement="placement"
  >
    <template slot="reference">
      <el-select
        ref="elSelect"
        @visible-change="visibleChange"
        :multiple="isMultiple"
        v-model="selectValue"
      >
        <template slot="empty">
          <div></div>
        </template>
      </el-select>
    </template>
    <el-tree
      v-on="treeEvents"
      :default-checked-keys="defaultCheckedKeys"
      :default-expanded-keys="expandedKeys"
      @check-change="treeCheckChange"
      @node-click="nodeClick"
      v-bind="mergeTreeProps"
      :show-checkbox="true"
      ref="elTree"
      :data="treeData"
    ></el-tree>
  </el-popover>
</template>

<script>
export default {
  name: "SelectTree",
  props: {
    value: {
      required: true
    },
    isMultiple: {
      type: Boolean,
      default: false
    },
    treeData: {
      type: Array,
      required: true,
      default() {
        return [];
      }
    },
    treeProps: {
      type: Object,
      default() {
        return {};
      }
    },
    treeEvents: {
      type: Object,
      default() {
        return {};
      }
    }
  },
  components: {},
  data() {
    return {
      popWidth: 150,
      placement: "bottom-start",
      baseTreeProps: {
        "check-strictly": true,
        "node-key": "id",
        "auto-expand-parent": true,
        "highlight-current": true,
        props: {
          label: "name"
        }
      }
    };
  },
  computed: {
    mergeTreeProps() {
      return { ...this.baseTreeProps, ...(this.treeProps ?? {}) };
    },
    defaultCheckedKeys() {
      let nodeKey = this.mergeTreeProps["node-key"];
      const res = this.value?.map(e => e[nodeKey]) ?? [];
      return res;
    },
    expandedKeys() {
      let res = this.findParentIds(this.treeData, this.defaultCheckedKeys);
      return res;
    },
    selectValue: {
      get() {
        if (Array.isArray(this.value)) {
          let labelStr = this.mergeTreeProps.props.label;
          if (this.isMultiple) {
            return this.value.map(e => e.name[labelStr]);
          } else {
            return this.value[0]?.[labelStr];
          }
        } else {
          return this.value;
        }
      },
      set(val) {
        this.$emit("input", val);
      }
    }
  },
  mounted() {},
  methods: {
    findParentIds(data, ids) {},
    nodeClick(data) {
      if (!this.isMultiple) {
        this.$refs.elTree.setChecked(data);
        let newData = { ...data };
        delete newData.children;
        this.selectValue = [newData];
      }
    },
    treeCheckChange(data) {
      console.log(this.$refs.elTree.getCheckedKeys());
    },
    visibleChange(val) {
      if (val) {
        this.popWidth = this.$refs.elSelect?.$el.getBoundingClientRect().width;
      }
    }
  }
};
</script>

<style lang="scss">
.select-tree-pop {
  box-sizing: border-box;
}
</style>
<style scoped lang="scss"></style>
