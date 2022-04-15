<script>
export default {
  name: "Stack",
  render(createElement, context) {
    const slots = this.$slots.default ?? [];

    return createElement(
      "div",
      { class: "stack" },
      slots.map(child => {
        return createElement("div", { class: "mt-4" }, [child]);
      })
    );
  }
};
</script>

<style scoped lang="scss">
.mt-4 {
  padding: 10px;
  text-align: left;
  outline: 1px solid red;
}
</style>
