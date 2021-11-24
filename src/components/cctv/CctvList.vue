<template>
  <b-container class="bv-example-row mt-3">
    <img
      src="@/assets/cctvimg1.png"
      class="d-inline-block align-middle"
      width="700px"
      alt="Kitten"
    />
    <b-row class="mb-1">
      <b-col class="sm-3">
        <b-form-select
          v-model="sidoCode"
          :options="sidos"
          @change="gugunList"
        ></b-form-select>
      </b-col>
      <b-col class="sm-3">
        <b-form-select
          v-model="gugunCode"
          :options="guguns"
          @change="gugunNames"
        ></b-form-select>
      </b-col>
    </b-row>
    <b-row>
      <b-col>
        <b-table-simple hover responsive>
          <b-thead head-variant="dark">
            <b-tr>
              <b-th>CCTV관리청</b-th>
              <b-th>CCTV위치</b-th>
              <b-th>관리 번호</b-th>
              <b-th>설치년도</b-th>
            </b-tr>
            <cctv-list-row
              v-for="(cctv, index) in cctvs"
              :key="index"
              v-bind="cctv"
            />
          </b-thead>
          <tbody></tbody>
        </b-table-simple>
      </b-col>
      <!-- <b-col v-else class="text-center">도서 목록이 없습니다.</b-col> -->
    </b-row>
  </b-container>
</template>

<script>
import { mapActions, mapMutations, mapState } from "vuex";
import CctvListRow from "@/components/cctv/CctvListRow";
const cctvStore = "cctvStore";
export default {
  name: "CctvList",
  data() {
    return {
      sidoName: "",
      gugunName: "",
      sidoCode: null,
      gugunCode: null,
    };
  },
  components: {
    CctvListRow,
  },
  computed: {
    ...mapState(cctvStore, ["cctvs", "sidos", "guguns"]),
  },
  created() {
    this.CLEAR_SIDO_LIST();
    this.getSido();
  },
  mounted() {},
  methods: {
    ...mapActions(cctvStore, [
      "getSido",
      "getGugun",
      "getCctvList",
      "detailCctv",
    ]),
    ...mapMutations(cctvStore, [
      "CLEAR_SIDO_LIST",
      "CLEAR_GUGUN_LIST",
      "SET_CCTV_LIST",
      "SET_DETAIL_CCTV",
    ]),
    gugunList() {
      for (let i = 0; i < this.sidos.length; i++) {
        if (this.sidos[i].value == this.sidoCode)
          this.sidoName = this.sidos[i].text;
      }
      this.CLEAR_GUGUN_LIST();
      this.gugunCode = null;
      if (this.sidoCode) this.getGugun(this.sidoCode);
    },
    gugunNames() {
      for (let i = 0; i < this.guguns.length; i++) {
        if (this.guguns[i].value == this.gugunCode)
          this.gugunName = this.guguns[i].text;
      }
      var add = this.sidoName + " " + this.gugunName + "청";
      var add1 = this.sidoName + " " + this.gugunName;
      this.getCctvList(add);
      this.getCctvList(add1);
    },
  },
};
</script>

<style scope>
.tdClass {
  width: 50px;
  text-align: center;
}
.tdSubject {
  width: 300px;
  text-align: left;
}
.table {
  background-color: white;
}
</style>
