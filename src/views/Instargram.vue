<template>
  <b-container class="bv-example-row mt-3 text-center">
    <h3 class="underline-green">
      <b-icon icon="instagram"></b-icon> SNS Service
    </h3>
    <b-row>
      <b-col></b-col>
      <b-col cols="10">
        <b-jumbotron
          bg-variant="muted"
          text-variant="dark"
          border-variant="dark"
        >
          <template #header><b>HappyHouse SNS</b></template>

          <template #lead> 홍보용 SNS </template>

          <hr class="my-4" />

          <p>사진을 클릭하여 계정을 방문해보세요.</p>
          <p><b>ssafy@instagram.com</b></p>
          <a href="https://www.instagram.com/hellossafy/?hl=ko">
            <img
              src="@/assets/instagram.jpg"
              class="d-inline-block align-middle"
              width="300px"
              alt="Kitten"
            />
          </a>
        </b-jumbotron>
      </b-col>
      <b-col></b-col>
    </b-row>
  </b-container>
</template>

<script>
export default {
  name: "Instargram",
};
</script>

<style scoped>
.underline-green {
  display: inline-block;
  background: linear-gradient(
    180deg,
    rgba(255, 255, 255, 0) 70%,
    rgba(56, 233, 40, 0.3) 30%
  );
}
</style>
