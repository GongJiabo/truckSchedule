<template>

  <p style="font-size:30px">人员管理</p>
  <div class="query">
    <div class="select">
      <el-select v-model="value1" class="m-2" placeholder="性别" size="large">
        <el-option
            v-for="item in options1"
            :key="item.value"
            :label="item.label"
            :value="item.value"
        />
      </el-select>
    </div>
    <div class="select">
      <el-select v-model="value2" class="m-2" placeholder="单位" size="large">
        <el-option
            v-for="item in options2"
            :key="item.value"
            :label="item.label"
            :value="item.value"
        />
      </el-select>
    </div>
    <div class="select">
      <el-select v-model="value3" class="m-2" placeholder="级别" size="large">
        <el-option
            v-for="item in options3"
            :key="item.value"
            :label="item.label"
            :value="item.value"
        />
      </el-select>
    </div>
    <el-button plain style="margin-left: 3%;width: 5%;height: 50%;">重置</el-button>
    <el-button type="primary" :icon="Search" style="margin-left: 3%;width: 5%;height: 50%;">查询</el-button>
  </div>

  <el-table :data="tableData" stripe style="width: 100%" size="large">
    <el-table-column prop="date" label="注册时间" width="180" />
    <el-table-column prop="name" label="人员姓名" width="180" />
    <el-table-column prop="phone" label="联系方式" width="220" />
    <el-table-column prop="address" label="地址" width="220" />
    <el-table-column prop="duty" label="当前职务"  width="180" />
    <el-table-column prop="attendance" label="本月缺勤/出勤" width="180"  />
    <el-table-column prop="operate" label="操作">
      <template #default>
        <el-button link type="primary" size="small" @click="handleClick">用户信息设置</el-button>
        <el-button link type="primary" size="small">查看历史情况</el-button>
      </template>
    </el-table-column>
  </el-table>

  <div class="example-pagination-block">
    <el-pagination layout="prev, pager, next" :total="50" />
  </div>
</template>

<script setup>
const tableData = [
  {
    date: '2016-05-03',
    name: 'Tom',
    address: 'No. 189, Grove St, Los Angeles',
    phone:'123456',
    duty: '工程师1级',
    attendance: '2/28'
  },
  {
    date: '2016-05-02',
    name: 'Tom',
    address: 'No. 189, Grove St, Los Angeles',
    phone:'123456',
    duty: '行程管理1级',
    attendance: '3/27'
  },
  {
    date: '2016-05-04',
    name: 'Tom',
    address: 'No. 189, Grove St, Los Angeles',
    phone:'123456',
    duty: '工程师2级',
    attendance: '2/28'
  },
  {
    date: '2016-05-01',
    name: 'Tom',
    address: 'No. 189, Grove St, Los Angeles',
    phone:'123456',
    duty: '行政管理2级',
    attendance: '2/28'
  },
  {
    date: '',
    name: '',
    address: '',
    phone:'',
    duty: '',
    attendance: ''
  },
  {
    date: '',
    name: '',
    address: '',
    phone:'',
    duty: '',
    attendance: ''
  },
]
</script>


<script>
export default {
name: "userConfig"
}
</script>

<style>
.query {
  position: relative;
  display: flex;
  align-items: center;
  background-color: #fff;
  height: 8%;
  border-radius: 8px;
  margin-bottom: 20px;
}

</style>

