<template>
  <div class="home">
    <Card class="card">
      <p slot="title">
        <span class="date">3/6</span> 标题
      </p>
      <div>
        <!-- <img src="../assets/logo.png" /> -->
        A high quality UI Toolkit based on Vue.js
      </div>
    </Card>

    <Card class="card">
      <p slot="title">
        <span class="date">3/6</span> 标题
      </p>
      <div>
        <!-- <img src="../assets/logo.png" /> -->
        A high quality UI Toolkit based on Vue.js
      </div>
    </Card>

    <Card class="card">
      <p slot="title">
        <span class="date">3/6</span> 标题
      </p>
      <div>
        <!-- <img src="../assets/logo.png" /> -->
        A high quality UI Toolkit based on Vue.js
      </div>
    </Card>

    <Card class="card">
      <p slot="title">
        <span class="date">3/6</span> 标题
      </p>
      <div>
        <!-- <img src="../assets/logo.png" /> -->
        A high quality UI Toolkit based on Vue.js
      </div>
    </Card>
  </div>
</template>

<script>
export default {
  name: "home",
  data() {
    return {
      haveLogin: true
    };
  },
  components: {},
  mounted() {
    // 用户是否登录
    this.isLogin();
    // 使用axios ，测试axios使用
    // this.axios.get("https://www.tianqiapi.com/api/?version=v1").then(
    //   res => {
    //     console.log(res);
    //   },
    //   err => {}
    // );

    this.axios
      .get("http://127.0.0.1:7002/dailylogin?username=wuzz&password=111")
      .then(
        res => {
          console.log(res);
        },
        err => {}
      );
  },
  methods: {
    // 判定是否登录
    isLogin() {
      if (!this.haveLogin) {
        this.$router.push({ name: "login" });
      }
    }
  }
};
</script>

<style lang="less">
.home {
  padding: 50px 0;

  .card {
    max-width: 480px;
    margin: 20px auto;
    .date {
      color: #989898;
    }
  }
}
</style>
