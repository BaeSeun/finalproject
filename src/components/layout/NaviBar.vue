<template>
  <div class="navv">
    <nav
      class="
        navbar navbar-light navbar-expand-md navbar-custom
        justify-content-center
      "
    >
      <router-link to="/">
        <img
          src="@/assets/ssafy_logo.png"
          class="d-inline-block align-middle"
          width="50px"
          alt="Kitten"
        />
      </router-link>
      <div
        class="
          navbar-collapse
          collapse
          justify-content-between
          align-items-center
          w-100
        "
        id="collapsingNavbar2"
      >
        <ul class="navbar-nav mx-auto text-center">
          <li class="nav-item active">
            <b-nav-item href="#"
              ><router-link :to="{ name: 'Home' }" class="link">
                홈</router-link
              ></b-nav-item
            >
          </li>
          <li class="nav-item">
            <b-nav-item href="#"
              ><router-link :to="{ name: 'Board' }" class="link">
                게시판</router-link
              ></b-nav-item
            >
          </li>
          <li class="nav-item">
            <b-nav-item href="#"
              ><router-link :to="{ name: 'Instargram' }" class="link">
                SNS</router-link
              ></b-nav-item
            >
          </li>
          <li class="nav-item">
            <b-nav-item href="#"
              ><router-link :to="{ name: 'House' }" class="link">
                아파트정보</router-link
              ></b-nav-item
            >
          </li>
        </ul>
        <ul class="nav navbar-nav flex-row justify-content-center flex-nowrap">
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
        </ul>
      </div>
    </nav>
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
  color: rgb(253, 165, 0);
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
