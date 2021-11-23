<template class="tofont">
  <b-container class="bv-example-row mt-3 text-center">
    <b-row>
      <b-col></b-col>
      <b-col cols="10">
        <b-jumbotron class="jumbo" text-variant="dark" border-variant="white">
          <template #header>
            <img
              src="@/assets/homeimg1.png"
              class="d-inline-block align-middle"
              width="100px"
              alt="Kitten"
            />
          </template>

          <template #lead> CCTV 페이지 입니다. <br /> </template>
          <cctv-list />
        </b-jumbotron>
      </b-col>
      <b-col></b-col>
    </b-row>
  </b-container>
</template>

<script>
import CctvList from "../components/cctv/CctvList.vue";

export default {
  name: "Cctv",
  props: {
    msg: String,
  },
  components: {
    CctvList,
  },
};
</script>

<style scoped>
.jumbo {
  background-color: #faed7d;
}
.tofont {
  font-family: "Jua", sans-serif;
}
</style>
