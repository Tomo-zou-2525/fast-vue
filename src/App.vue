<template>
  <div>
    <p v-if="msg.length > 0">
      {{ msg }}
    </p>
    <p v-else>No text</p>
    <input type="text" v-model="msg" />
    <button @click="allDelete()">AllDelete</button>
  </div>
</template>

<script>
export default {
  data() {
    return {
      msg: "Hello Unko",
    };
  },
  methods: {
    allDelete: function () {
      this.msg = "";
    },
  },
};
</script>
