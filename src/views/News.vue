<template>
  <b-container class="bv-example-row mt-3 text-center">
    <b-row>
      <b-col></b-col>
      <b-col cols="10">
        <b-jumbotron
          class="jumbo"
          bg-variant="muted"
          text-variant="dark"
          border-variant="light"
        >
          <template #header>
            <img
              src="@/assets/newsimg3.png"
              class="d-inline-block align-middle"
              width="800px"
              alt="Kitten"
          /></template>

          <!-- <template #lead> 홍보용 SNS </template> -->

          <hr class="my-4" />
          <img
            src="@/assets/newsimg1.png"
            class="d-inline-block align-middle"
            width="800px"
            alt="Kitten"
          />
          <img
            src="@/assets/newsimg2.png"
            class="d-inline-block align-middle"
            width="800px"
            alt="Kitten"
          />

          <p>사진을 클릭하여 계정을 방문해보세요.</p>
          <p><b>ssafy@instagram.com</b></p>
          <a href="https://www.instagram.com/hellossafy/?hl=ko">
            <img
              src="@/assets/instagramimg1.png"
              class="d-inline-block align-middle"
              width="600px"
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
  name: "News",
};
</script>

<style scoped>
.jumbo {
  background-color: rgb(241, 207, 213);
}
</style>
