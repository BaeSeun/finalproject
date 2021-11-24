<template>
  <b-container v-if="house" class="bv-example-row">
    <b-row>
      <b-col
        ><h3>{{ house.아파트 }}</h3></b-col
      >
    </b-row>
    <b-row class="mb-2 mt-1">
      <div>
        <div id="map"></div>
      </div>
    </b-row>
    <img
      src="@/assets/aptdetailimg1.png"
      class="d-inline-block align-left"
      width="500px"
      alt="Kitten"
    />
    <b-row>
      <table class="table table-bordered">
        <thead>
          <tr class="table-success">
            <th scope="col">일련번호</th>
            <th scope="col">법정동</th>
            <th scope="col">층수</th>
            <th scope="col">거래금액</th>
          </tr>
        </thead>
        <tbody>
          <tr>
            <th scope="row">{{ house.일련번호 }}</th>
            <td>{{ house.법정동 }}</td>
            <td>{{ house.층 }}층</td>
            <td>
              {{
                (parseInt(house.거래금액.replace(",", "")) * 10000) | price
              }}원
            </td>
          </tr>
        </tbody>
      </table>
    </b-row>
    <b-row> </b-row>
  </b-container>
</template>

<script>
import { mapState } from "vuex";

const houseStore = "houseStore";

export default {
  name: "HouseDetail",
  computed: {
    ...mapState(houseStore, ["house"]),
    // house() {
    //   return this.$store.state.house;
    // },
  },
  data() {
    return {
      map: null,
      markerPositions1: [],
      markers: [],
      infowindow: null,
    };
  },
  updated() {
    this.initMap();
    this.add = this.house.법정동 + " " + this.house.지번;
    this.apt = this.house.아파트;
    this.geocoder = new kakao.maps.services.Geocoder();
    this.geocoder.addressSearch(this.add, (result, status) => {
      // 정상적으로 검색이 완료됐으면
      if (status === kakao.maps.services.Status.OK) {
        var coords = new kakao.maps.LatLng(result[0].y, result[0].x);
        this.markerPositions1.push(coords);
        var marker = new kakao.maps.Marker({
          map: this.map,
          position: coords,
        });
        var infowindow = new kakao.maps.InfoWindow({
          content:
            '<div style="width:150px;text-align:center;padding:6px 0;">' +
            this.apt +
            "</div>",
        });
        infowindow.open(this.map, marker);
        this.map.setCenter(coords);
      }
    });
  },
  mounted() {
    if (window.kakao && window.kakao.maps) {
      this.initMap();
    } else {
      const script = document.createElement("script");
      /* global kakao */
      script.onload = () => kakao.maps.load(this.initMap);
      script.src =
        "//dapi.kakao.com/v2/maps/sdk.js?autoload=false&appkey=915cffed372954b7b44804ed422b9cf0&libraries=services";
      document.head.appendChild(script);
    }
  },
  methods: {
    initMap() {
      const container = document.getElementById("map");
      const options = {
        center: new kakao.maps.LatLng(33.450701, 126.570667),
        level: 5,
      };
      this.map = new kakao.maps.Map(container, options);
    },
  },
  filters: {
    price(value) {
      if (!value) return value;
      return value.toString().replace(/\B(?=(\d{3})+(?!\d))/g, ",");
    },
  },
};
</script>

<style>
#map {
  width: 540px;
  height: 400px;
}
</style>
