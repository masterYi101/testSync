<template>
  <div class="home">
    <HelloWorld>
      <h1 slot="bbb">我是插槽aaa</h1>
      <h1 slot="aaa" slot-scope="{vm}">我是插槽bbb {{vm}}</h1>
    </HelloWorld>
  </div>
</template>

<script>
// @ is an alias to /src
import HelloWorld from "@/components/HelloWorld.vue";
import { a, b } from "@/test/test";
console.log(a, b);
export default {
  name: "Home",
  components: {
    HelloWorld
  },
  methods: {}
};
</script>
