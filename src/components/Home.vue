<template>
  <div>
    <div v-if="pageNumber == 1">
      <FirstPage />
    </div>
    <div v-if="pageNumber == 2">
      <SecondPage />
    </div>
    <div v-if="pageNumber == 3">
      <ThirdPage />
    </div>
  </div>
</template>

<script>
import FirstPage from "../components/FirstPage.vue";
import SecondPage from "../components/SecondPage.vue";
import ThirdPage from "../components/ThirdPage.vue";

export default {
  name: "home",
  components: {
    FirstPage,
    SecondPage,
    ThirdPage,
  },
  data() {
    return {
      pageNumber: 1,
    };
  },
};
</script>

<style></style>
