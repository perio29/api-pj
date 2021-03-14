<template>
  <div class="home">
    <input type="text" v-model="zipcode">
    <button @click="onClick">住所自動入力</button>
    <p>Address : {{ addressData }}</p>
  </div>
</template>

<script>
import axios from "axios";
export default {
  data() {
    return {
      zipcode: '',
      addressData: ''
    }
  },
  methods: {
    onClick() {
      axios.get(`https://apis.postcode-jp.com/api/v4/postcodes/${this.zipcode}?gvVLQ9EhwtqL2zePjeeJaU2KTZkfGjoA5MLHAUP`).then((res) => {
        this.addressData = res.data[0].allAddress;
      })
    }

    }
};

</script>

<style>
input {
  padding: 1px 2px;
  text-align: start;
}

button {
  color: black, white;
  display: inline-block;
  align-items: flex-start;
  background-color: rgb(239, 239, 239), rgb(59, 59, 59);
}

p {
    display: block;
    font-size: 16px;
    font-weight:normal;
    margin-block-start: 1em;
    margin-block-end: 1em;
    margin-inline-start: 0px;
    margin-inline-end: 0px;
}
</style>