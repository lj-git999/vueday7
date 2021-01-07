<template>
  <div>
    <el-row :gutter="20">
      <el-col :span="8"><div class="grid-content bg-purple">&nbsp;</div></el-col>
      <el-col :span="8"><div class="grid-content bg-purple">
        <el-form :model="user" status-icon ref="urs" label-width="100px" class="demo-ruleForm">
        <el-form-item label="id" prop="id">
          <el-input type="text" v-model="user.id" autocomplete="off"></el-input>
        </el-form-item>
        <el-form-item label="姓名" prop="checkPass">
          <el-input type="text" v-model="user.username" autocomplete="off"></el-input>
        </el-form-item>
        <el-form-item label="年龄" prop="age">
          <el-input v-model.number="user.age"></el-input>
        </el-form-item>
        <el-form-item label="省份" prop="province">
          <el-input v-model="user.province "></el-input>
        </el-form-item>
        <el-form-item label="日期" prop="date">
          <el-date-picker type="date" placeholder="选择日期" v-model="user.date" style="width: 100%;" value-format="yyyy - MM - dd "></el-date-picker>
        </el-form-item>
        <el-form-item label="邮箱" prop="email">
          <el-input v-model="user.email"></el-input>
        </el-form-item>
        <el-form-item>
          <el-button type="primary" @click="submitForm('user')">提交</el-button>
          <el-button @click="resetForm('user')">重置</el-button>
        </el-form-item>
      </el-form></div></el-col>
      <el-col :span="8"><div class="grid-content bg-purple">&nbsp;</div></el-col>
    </el-row>

  </div>

</template>

<script>
export default {
  name: "Second",
  data() {
    return {
      user: {},
    }
  },
  methods: {
    submitForm() {
      conLSearcsole.log(this.user.username)
      let params = new URhParams();
      params.append('username', this.user.username,);
      params.append('age', this.user.age,);
      params.append('province', this.user.province,);
      params.append('date', this.user.date,);
      params.append('email', this.user.email,);

      this.$axios({
        url: "http://127.0.0.1:8000/userapp/add/",
        method: "post",
        data: params,
        xml
      }).then(rst => {
        console.log(rst.data);
        alert(rst.data.message);
      }).catch(error => {
        console.log(error);
      })
    }
  }
}
</script>

<style scoped>

</style>
