<template>
  <div class="wrap">
    <h1>登录</h1>
    <div class="input_box">
      用户名：
      <Input class="input" v-model="name" placeholder="请输入用户名" />
    </div>
    <div class="input_box">
      密码：
      <Input class="input" type="password" v-model="pass" placeholder="请输入密码" />
    </div>
    <div class="input_box">
      <Button type="primary" @click="login" long>登录</Button>
    </div>
  </div>
</template>

<script>
export default {
  data() {
    return {
      name: "",
      pass: ""
    };
  },
  methods: {
    // 登录
    login() {
      if (!this.name || !this.pass) {
        this.$Notice.open({
          title: "警告",
          desc: "用户名和密码不能为空"
        });
        return;
      }
      // 发送请求
      this.axios
        .get("http://127.0.0.1:7002/dailylogin", {
          params: {
            username: this.name,
            password: this.pass
          }
        })
        .then(
          res => {
            console.log("成功", res);
          },
          err => {
            console.log("失败", err);
          }
        );
    }
  }
};
</script>

<style lang="less">
.wrap {
  width: 400px;
  margin: 20px auto;
  // text-align: center;

  h1 {
    text-align: center;
  }
  .input {
    width: 100%;
  }
  .input_box {
    margin: 20px 0;
  }
}
</style>