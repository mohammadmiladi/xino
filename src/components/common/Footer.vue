<template>
  <div @click="goToMohammadSite()" class="footer-style">
    Copyright 2022 Mohammad Miladi
  </div>
</template>

<script>
export default {
  name: "footer-page",
  methods: {
    goToMohammadSite() {
      window.open("https://mohammadmiladi.ir", "_blank");
    },
  },
};
</script>

<style>
.footer-style {
  display: flex;
  justify-content: center;
  align-items: center;
  padding: 7px;
  position: fixed;
  bottom: 0;
  color: blue;
  font-size: 20px;
  width: 100%;
  height: 20px;
  background: rgb(214, 214, 255);
}
.footer-style:hover {
  text-decoration: underline;
  cursor: pointer;
}
</style>
