<template>
  <el-table :data="tableData" height="250" style="width: 100%" size="large">
    <el-table-column prop="date" label="日期" width="180" />
    <el-table-column prop="name" label="规则名称" width="180" />
    <el-table-column prop="people" label="人员" width="180" />
    <el-table-column prop="content" label="自动回复内容" />
    <el-table-column prop="time" label="回复时间" />
    <el-table-column label="Operations" width="120">
      <template #default>
        <el-button link type="primary" size="small" @click="handleClick"
        >Detail</el-button
        >
        <el-button link type="primary" size="small">Edit</el-button>
      </template>
    </el-table-column>
  </el-table>

  <el-form :model="form" label-width="120px" size="large">
    <el-form-item >
    </el-form-item>

    <el-form-item label="自动回复主题">
      <el-input v-model="form.name" />
    </el-form-item>
    <el-form-item label="回复人员">
      <el-select v-model="form.region" placeholder="please select">
        <el-option label="Zone one" value="shanghai" />
        <el-option label="Zone two" value="beijing" />
      </el-select>
    </el-form-item>
    <el-form-item label="自动回复时间">
      <el-col :span="11">
        <el-date-picker
            v-model="form.date1"
            type="date"
            placeholder="Pick a date"
            style="width: 100%"
        />
      </el-col>
      <el-col :span="2" class="text-center">
        <span class="text-gray-500">-</span>
      </el-col>
      <el-col :span="11">
        <el-time-picker
            v-model="form.date2"
            placeholder="Pick a time"
            style="width: 100%"
        />
      </el-col>
    </el-form-item>
    <el-form-item label="关键词回复">
      <el-switch v-model="form.delivery" />
    </el-form-item>
    <el-form-item label="回复类型">
      <el-radio-group v-model="form.resource">
        <el-radio label="通知" />
        <el-radio label="警告" />
      </el-radio-group>
    </el-form-item>
    <el-form-item label="回复内容">
      <el-input v-model="form.desc" type="textarea" />
    </el-form-item>
    <el-form-item>
      <el-button type="primary" @click="onSubmit">Create</el-button>
      <el-button>Cancel</el-button>
    </el-form-item>
  </el-form>
</template>
e>

<script>
export default {
  name: "autoReply"
}
</script>
<script setup>
import { reactive } from 'vue'

// do not use same name with ref
const form = reactive({
  name: '',
  region: '',
  date1: '',
  date2: '',
  delivery: false,
  type: [],
  resource: '',
  desc: '',
})

const onSubmit = () => {
  console.log('submit!')
}

const handleClick = () => {
  console.log('click')
}

const tableData = [
  {
    date: '2016-05-03',
    name: 'reply1',
    people: '李四',
    content: '感谢你的咨询，请等待进一步通知',
    time: '2016-05-04 23:00 - 2016-05-04 21:00'
  },
  {
    date: '2016-05-03',
    name: 'reply1',
    people: '王五',
    content: '感谢你的咨询，请等待进一步通知',
    time: '2016-05-04 23:00 - 2016-05-04 21:00'
  },
  {
    date: '2016-05-03',
    name: 'reply1',
    content: '感谢你的咨询，请等待进一步通知',
    time: '2016-05-04 23:00 - 2016-05-04 21:00'
  },
  {
    date: '2016-05-03',
    name: 'reply1',
    content: '感谢你的咨询，请等待进一步通知',
    time: '2016-05-04 23:00 - 2016-05-04 21:00'
  }
]
</script>

<style scoped>

</style>