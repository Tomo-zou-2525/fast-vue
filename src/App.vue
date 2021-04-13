<template>
  <div>
    <myheader></myheader>
    <p v-if="msg.length > 0">
      {{ msg }}
    </p>
    <p v-else>No text</p>
    <input type="text" v-model="msg" />
    <button @click="allDelete()">AllDelete</button>
    <!-- <button @click="getApi">API取得</button> -->
  </div>
</template>

<script>
import myheader from "./components/myHeader";

export default {
  components: {
    myheader,
  },
  data() {
    return {
      msg: "Hello Unko",
    };
  },
  methods: {
    allDelete: function () {
      this.msg = "";
    },
    // getApi: function () {
    //   fetch(
    //     "http://www.geonames.org/postalCodeLookupJSON?postalcode=10504&country=US"
    //   )
    //     .then((response) => {
    //       return response.json();
    //     })
    //     .then((json) => {
    //       this.msg = json.postalcodes[0].adminName1;
    //     })
    //     .catch((err) => {
    //       this.msg = err;
    //     });
    // },
  },
  created() {
    fetch(
      "http://www.geonames.org/postalCodeLookupJSON?postalcode=10504&country=US"
    )
      .then((response) => {
        return response.json();
      })
      .then((json) => {
        this.msg = json.postalcodes[0].adminName1;
      })
      .catch((err) => {
        this.msg = err; // エラー処理
      });
  },
};
</script>
