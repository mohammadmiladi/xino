<template>
  <div class="main-first">
    <button @click="nextPage()" class="button-style">شروع</button>
  </div>
</template>

<script>
export default {
  name: "firstPage",
  methods: {
    nextPage() {
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
  background: rgb(21, 21, 165);
  color: white;
  font-weight: 700;
  border: 2px solid white;
  border-radius: 5px;
  font-size: 18px;
}
.button-style:hover {
  background: rgb(195, 206, 255);
  color: rgb(21, 21, 165);
  border: 2px solid rgb(21, 21, 165);
  cursor: pointer;
}
</style>
