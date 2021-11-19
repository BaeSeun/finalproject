<template>
  <div class="navv">
    <b-navbar toggleable="lg" type="dark" class="navbar navbar-custom">
      <b-navbar-toggle target="nav-collapse"></b-navbar-toggle>

      <b-collapse id="nav-collapse" is-nav>
        <b-navbar-nav class="nav navbar-nav">
          <b-nav-item href="#"
            ><router-link :to="{ name: 'Home' }" class="link">
              홈</router-link
            ></b-nav-item
          >
          <b-nav-item href="#"
            ><router-link :to="{ name: 'Board' }" class="link">
              게시판</router-link
            ></b-nav-item
          >
          <b-nav-item href="#"
            ><router-link :to="{ name: 'Instargram' }" class="link">
              SNS</router-link
            ></b-nav-item
          >
          <b-nav-item href="#"
            ><router-link :to="{ name: 'House' }" class="link">
              아파트정보</router-link
            ></b-nav-item
          >
        </b-navbar-nav>
        <b-navbar-brand href="#" class="navbar-brand mx-auto">
          <router-link to="/">
            <img
              src="@/assets/ssafy_logo.png"
              class="d-inline-block align-middle"
              width="50px"
              alt="Kitten"
            />
          </router-link>
        </b-navbar-brand>
        <b-navbar-nav class="nav navbar-nav ml-auto">
          <b-nav-item-dropdown right>
            <template #button-content>
              <b-icon icon="people" font-scale="2"></b-icon>
            </template>
            <b-dropdown-item href="#"
              ><router-link :to="{ name: 'SignUp' }" class="link"
                ><b-icon icon="person-circle"></b-icon> 회원가입</router-link
              ></b-dropdown-item
            >
            <b-dropdown-item href="#"
              ><router-link :to="{ name: 'SignIn' }" class="link"
                ><b-icon icon="key"></b-icon> 로그인</router-link
              ></b-dropdown-item
            >
          </b-nav-item-dropdown>
        </b-navbar-nav>
      </b-collapse>
    </b-navbar>
  </div>
</template>

<script>
export default {
  name: "NaviBar",
};
</script>

<style>
.navbar-custom {
  background-color: #f0ca61;
}
a:visited {
  color: pink;
  background-color: transparent;
  text-decoration: none;
}
.navbar-header {
  float: left;
  padding: 15px;
  text-align: center;
  width: 100%;
}
.navbar-brand {
  float: none;
}
</style>
