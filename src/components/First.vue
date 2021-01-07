<template>
  <div>
    <el-container>
      <el-header>百知学员信息管理系统</el-header>
      <el-main><el-table :data="user_dict" border style="width: 100%">
        <el-table-column  prop="id" label="id" width="150"></el-table-column>
        <el-table-column prop="username" label="姓名" width="120"></el-table-column>
        <el-table-column prop="age" label="年龄" width="120"></el-table-column>
        <el-table-column prop="province" label="省份" width="120"></el-table-column>
          <el-table-column label="日期" width="180">
            <template slot-scope="scope">
              <i class="el-icon-time"></i>
              <span style="margin-left: 10px">{{ scope.row.date }}</span>
            </template>
          </el-table-column>
        <el-table-column prop="email" label="邮箱" width="120"></el-table-column>
        <el-table-column label="操作">
          <template slot-scope="scope">
            <el-button size="mini" @click="handleAdd(scope.$index, scope.row.id)">增加</el-button>
            <el-button size="mini" type="danger" @click="handleShow(scope.$index, scope.row.id)">查看</el-button>
          </template>
        </el-table-column>
      </el-table></el-main>
      <el-footer>Footer</el-footer>
    </el-container>
  </div>

</template>

<script>
export default {
  name: "First",
  methods: {
    handleAdd(index, row) {
      console.log(index, row);
      this.$router.push("/second/"+row);
    },
    handleShow(index, row) {
      console.log(index, row);
      this.$router.push("/third/"+row);
    }
  },

  data() {
    return {
      user_dict: [],
    }
  },
  created() {
    this.$axios({
      url:"http://127.0.0.1:8000/userapp/get/",
      method:"get",
    }).then(rst=>{
      console.log(rst.data.result);
      this.user_dict=rst.data.result;
    }).catch(error=>{
      console.log(error);
    })
  }
}
</script>

<style scoped>
.el-header, .el-footer {
  background-color: mediumaquamarine;
  color: #333;
  text-align: center;
  line-height: 60px;
}

.el-aside {
  background-color: #D3DCE6;
  color: #333;
  text-align: center;
  line-height: 200px;
}

.el-main {
  background-color: lightsteelblue;
  color: #333;
  text-align: center;
  line-height: 60px;
}

body > .el-container {
  margin-bottom: 40px;
}

.el-container:nth-child(5) .el-aside,
.el-container:nth-child(6) .el-aside {
  line-height: 260px;
}

.el-container:nth-child(7) .el-aside {
  line-height: 320px;
}
</style>
