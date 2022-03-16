<template>
  <div class="home">
    <HelloWorld key="123"> </HelloWorld>
  </div>
</template>

<script>
// @ is an alias to /src
import HelloWorld from "@/components/HelloWorld.vue";
export default {
  name: "Home",
  props: {
    aaa: {
      type: String,
      default() {
        return this.aa;
      }
    }
  },
  data() {
    return {
      aa: 1
    };
  },
  mounted() {
    setTimeout(() => {
      this.aa = 100;
    }, 1000);
  },
  components: {
    HelloWorld
  },
  methods: {}
};
</script>
