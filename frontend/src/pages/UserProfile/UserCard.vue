<template>
  <card class="card-user">
    <div slot="image">
      <img src="@/assets/img/dotz.png" style="margin-top: -155px" alt="...">
    </div>
    <div>
      <div class="author">
        <img class="avatar border-white" :src="require('@/assets/img/' + this.$store.state.walletInfo.imgPath)" alt="...">
        <h4 class="title">{{this.$store.state.walletInfo.email}}
          <br>
            <small>{{this.$store.state.walletInfo.address}}</small>
        </h4>
      </div>
      <p class="description text-center">
        <br> <br>
      </p>
    </div>
    <hr>
    <div class="text-center">
      <br>
      <div class="row">
        <div v-for="(info, index) in details" :key="index" :class="getClasses(index)">
          <h5>{{info.title}}
            <br>
            <small>{{info.subTitle}}</small>
          </h5>
        </div>
      </div>
    </div>
  </card>
</template>
<script>

export default {
  data() {
    return {
      details: [
        {
          title: this.$store.state.walletInfo.transactions,
          subTitle: "Transactions"
        },
        {
          title: this.$store.state.walletInfo.tokenAmount,
          subTitle: "$DAG"
        },
        {
          title: this.$store.state.walletInfo.usdValue,
          subTitle: "USD"
        }
      ]
    };
  },
  methods: {
    getClasses(index) {
      var remainder = index % 3;
      if (remainder === 0) {
        return "col-lg-3 offset-lg-1";
      } else if (remainder === 2) {
        return "col-lg-4";
      } else {
        return "col-lg-3";
      }
    }
  }
};
</script>
<style>
</style>
