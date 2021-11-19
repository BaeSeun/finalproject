<template>
  <b-container class="bv-example-row mt-3">
    <b-row>
      <b-col>
        <b-alert variant="secondary" show><h3>회원가입</h3></b-alert>
      </b-col>
    </b-row>
    <register-form />
  </b-container>
</template>

<script>
import RegisterForm from "./child/RegisterForm.vue";
export default {
  name: "MemberJoin",
  components: {
    RegisterForm,
  },
};
</script>

<style></style>
