<template>
  <div class="main-first">
    <button @click="firstPage()" class="button-style">تلاش مجدد</button>
  </div>
</template>

<script>
export default {
  name: "firstPage",
  methods: {
    firstPage() {
      this.$emit("changePage");
    },
  },
};
</script>

<style scoped>
.main-first {
  width: 100%;
  min-height: 100vh;
  max-height: 100vh;
  background: rgb(206, 206, 206);
  display: flex;
  justify-content: center;
  align-items: center;
}
.button-style {
  padding: 10px 30px;
  background: rgb(31, 165, 53);
  color: white;
  font-weight: 700;
  border: 2px solid white;
  border-radius: 5px;
  font-size: 18px;
}
.button-style:hover {
  background: rgb(195, 206, 255);
  color: rgb(10, 212, 70);
  border: 2px solid rgb(0, 243, 0);
  cursor: pointer;
}
</style>
