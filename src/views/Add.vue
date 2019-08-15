
<template>
  <div>
    <div class="form-item">
      标题:
      <Input v-model="title" placeholder="请输入标题" />
    </div>
    <div class="form-item">
      内容:
      <Input v-model="content" type="textarea" placeholder="请输入日记内容" />
    </div>
    <div class="form-item">
      <Button ype="primary" @click="add">提交</Button>
    </div>
  </div>
</template>

<script>
export default {
  data() {
    return {
      title: "",
      content: "",
      csrftoken: ""
    };
  },
  mounted() {
    this.csrftoken = this.$cookies.get("csrfToken");
  },
  methods: {
    add() {
      // 未提交成功，csrf问题，暂时解决不了
      axios
        .post(
          `http://127.0.0.1:7002/dailyadd`,
          {
            title: this.title,
            content: this.content
          },
          {
            headers: {
              "x-csrf-token": this.csrftoken
            }
          }
        )
        .then(function(res) {
          console.log(res);
        })
        .catch(function(err) {
          console.log(err);
        });
    }
  }
};
</script>

<style lang="less">
.form-item {
  margin: 30px auto;
  max-width: 500px;
}
</style>