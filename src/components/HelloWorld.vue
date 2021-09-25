<template>
  <div class="div">
    <slot v-for="(vnode, key) in dtSlots" :name="key" :vm="123"></slot>
  </div>
</template>

<script>
export default {
  name: "HelloWorld",
  props: {
    msg: String
  },
  data() {
    return {
      rTime: 20,
      sTime: 19,
      cacheTime: 0
    };
  },
  computed: {
    dtSlots() {
      let res = {};
      Object.keys(this.$scopedSlots).forEach(e => {
        if (e === "aaa") {
          res[e] = this.$slots[e];
        }
      });
      return res;
    }
  },
  mounted() {
    console.log(this);
  },
  methods: {
    test() {
      console.log(1);
    },
    openTime() {
      const test = () => {
        const aaa = time => {
          if (time - this.cacheTime >= 1000) {
            this.rTime -= 1;
            this.cacheTime = time;
          }
          window.requestAnimationFrame(aaa);
        };
        window.requestAnimationFrame(aaa);
      };
      test();
      setInterval(() => {
        this.sTime -= 1;
      }, 1000);
    },
    openLang() {
      for (let i = 1; i < 100000; i++) {
        console.log(i);
      }
    }
  }
};
</script>

<style scoped lang="scss">
@import url("//at.alicdn.com/t/font_2411645_2c7zja5bkxp.css");
div {
  display: flex;

  color: red;
}
</style>
