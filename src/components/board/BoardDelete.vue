<template>
  <b-container class="bv-example-row mt-3">
    <b-row>
      <b-col>
        <b-alert show><h3>질문 목록</h3></b-alert>
      </b-col>
    </b-row>
    <b-row>
      <b-col><b-alert show variant="danger">삭제중/b-alert></b-col>
    </b-row>
  </b-container>
</template>

<script>
import http from "@/util/http-common";

export default {
  name: "BoardDelete",
  created() {
    http.delete(`/board/${this.$route.params.articleno}`).then(({ data }) => {
      let msg = "삭제 중 문제 발생";
      if (data === "success") {
        msg = "삭제 완료";
      }
      alert(msg);
      // 현재 route를 /list로 변경.
      this.$router.push({ name: "BoardList" });
    });
  },
};
</script>

<style></style>
