<template>
  <b-container class="bv-example-row mt-3">
    <img
      src="@/assets/loginimg1.png"
      class="d-inline-block align-middle"
      width="400px"
      alt="Kitten"
    />

    <b-row class="align-middle">
      <b-col></b-col>
      <b-col cols="5">
        <b-card
          class="text-center mt-3 bg-transparent border-0 align-middle"
          style="max-width: 30rem height: 50px"
        >
          <b-form class="text-left">
            <b-alert show variant="danger" v-if="isLoginError"
              >아이디 또는 비밀번호를 확인하세요.</b-alert
            >
            <b-form-group label="아이디" label-for="userid">
              <b-form-input
                id="userid"
                v-model="user.userid"
                required
                placeholder="아이디를 입력하세요."
                @keyup.enter="confirm"
              ></b-form-input>
            </b-form-group>
            <b-form-group label="비밀번호" label-for="userpwd">
              <b-form-input
                type="password"
                id="userpwd"
                v-model="user.userpwd"
                required
                placeholder="비밀번호를 입력하세요."
                @keyup.enter="confirm"
              ></b-form-input>
            </b-form-group>
            <b-col class="text-center">
              <b-button
                type="button"
                variant="dark"
                class="m-1"
                @click="confirm"
                align="center"
                >로그인</b-button
              >
              <b-button
                type="button"
                variant="dark"
                class="m-1"
                @click="movePage"
                align="center"
                >회원가입</b-button
              >
            </b-col>
          </b-form>
        </b-card>
      </b-col>
      <b-col></b-col>
    </b-row>
  </b-container>
</template>

<script>
import { mapState, mapActions } from "vuex";

const memberStore = "memberStore";

export default {
  name: "MemberLogin",
  data() {
    return {
      user: {
        userid: null,
        userpwd: null,
      },
    };
  },
  computed: {
    ...mapState(memberStore, ["isLogin", "isLoginError"]),
  },
  methods: {
    ...mapActions(memberStore, ["userConfirm", "getUserInfo"]),
    async confirm() {
      await this.userConfirm(this.user);
      let token = sessionStorage.getItem("access-token");
      if (this.isLogin) {
        await this.getUserInfo(token);
        this.$router.push({ name: "Home" });
      }
    },
    movePage() {
      this.$router.push({ name: "SignUp" });
    },
  },
};
</script>

<style>
.loginimg {
  align-content: center;
}
</style>
