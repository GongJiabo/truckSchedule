<template>
  <div class="main">
    <div class="query">
      <div class="select">
        <el-select v-model="value1" class="m-2" placeholder="人员姓名" size="large">
          <el-option
              v-for="item in options1"
              :key="item.value"
              :label="item.label"
              :value="item.value"
          />
        </el-select>
      </div>
      <div class="select">
        <el-select v-model="value2" class="m-2" placeholder="人员编号" size="large">
          <el-option
              v-for="item in options2"
              :key="item.value"
              :label="item.label"
              :value="item.value"
          />
        </el-select>
      </div>
      <div class="select">
        <el-select v-model="value3" class="m-2" placeholder="所处地点" size="large">
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
    <div class="table">
      <el-table :data="tableData" border size="large">
        <el-table-column fixed prop="choose" label="群发" min-width="1.5" >
          <el-checkbox v-model="checked1" size="large" />
        </el-table-column>

        <el-table-column fixed prop="number" label="人员编号" min-width="2">
          <template #default="scope">
            <el-popover effect="light" trigger="hover" placement="top" width="auto">
              <template #reference>
                <el-tag>{{ scope.row.number }}</el-tag>
              </template>
            </el-popover>
          </template>
        </el-table-column>
        <el-table-column prop="name" label="人员姓名" min-width="2" />
        <el-table-column prop="phone" label="联系方式" min-width="2" />
        <el-table-column prop="state" label="当前状态" min-width="2" />
        <el-table-column prop="manage" label="名下车辆" min-width="3" />
        <el-table-column prop="position" label="车辆位置" min-width="5" />
        <el-table-column fixed="right" label="操作" min-width="3">
          <template #default>
            <el-button link type="primary" size="small" @click="handleClick">短信编辑</el-button>
            <el-button link type="primary" size="small">历史信息</el-button>
          </template>
        </el-table-column>
      </el-table>
    </div>

    <!--  jbgong added:  -->
    <div class="form">
      <el-form :model="form" label-width="120px"  border size="large">
        <el-form-item label="人员姓名">
          <el-input v-model="form.name" />
        </el-form-item>
        <el-form-item label="短信运营商">
          <el-select v-model="form.region" placeholder="please select your zone">
            <el-option label="电信" value="shanghai" />
            <el-option label="移动" value="beijing" />
            <el-option label="联通" value="beijing" />
          </el-select>
        </el-form-item>
        <el-form-item label="发送时间">
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
        <el-form-item label="是否定时发送">
          <el-switch v-model="form.delivery" />
        </el-form-item>
        <el-form-item label="短信类型">
          <el-checkbox-group v-model="form.type">
            <el-checkbox label="工作提醒" name="type" />
            <el-checkbox label="新工作安排" name="type" />
            <el-checkbox label="临时调度" name="type" />
            <el-checkbox label="紧急通知" name="type" />
          </el-checkbox-group>
        </el-form-item>
        <el-form-item label="短信内容">
          <el-input v-model="form.desc" type="textarea" />
        </el-form-item>
        <el-form-item>
          <el-button type="primary" @click="onSubmit">发送</el-button>
          <el-button>取消</el-button>
        </el-form-item>
      </el-form>
    </div>
  </div>

</template>

<script>
export default {
  name: "sendMessage"
}
</script>

<script setup>

import {
  Search
} from '@element-plus/icons-vue'
import {ref} from "vue";
import { reactive } from 'vue'

const num_input = ref('')
const value1 = ref('')
const value2 = ref('')
const value3 = ref('')
const options1 = [
  {
    value: 'Option1',
    label: 'Option1',
  },
  {
    value: 'Option2',
    label: 'Option2',
  },
]
const options2 = [
  {
    value: 'Option1',
    label: 'Option1',
  },
  {
    value: 'Option2',
    label: 'Option2',
  },
  {
    value: 'Option3',
    label: 'Option3',
  },

]
const options3 = [
  {
    value: 'Option1',
    label: 'Option1',
  },
  {
    value: 'Option2',
    label: 'Option2',
  },
  {
    value: 'Option3',
    label: 'Option3',
  },
]

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

const tableData = [
  {
    number: 'WH110',
    name: '张三',
    phone: '123456',
    state: '工作中',
    manage: '卡车#1',
    position: 'No. 189, Grove St, Los Angeles',
    tag: 'Home',
  },
  {
    number: 'WH001',
    phone: '135792',
    name: '李四',
    state: '空闲',
    manage: '挖掘机#1',
    position: 'No. 189, Grove St, Los Angeles',
    tag: 'Office',
  },
  {
    number: 'GZ002',
    name: '王五',
    phone: '123456',
    state: '工作中',
    manage: '挖掘机#2',
    position: 'No. 189, Grove St, Los Angeles',
    tag: 'Home',
  },
  {
    number: 'HS123',
    name: '赵六',
    phone: '123456',
    state: '工作中',
    manage: '压路机#4',
    position: 'No. 189, Grove St, Los Angeles',
    tag: 'Office',
  },
  {
    number: 'HS123',
    name: '孙七',
    phone: '654321',
    state: '休假中',
    manage: '压路机#4',
    position: 'No. 189, Grove St, Los Angeles',
    tag: 'Office',
  }
]
</script>

<style lang='scss'>

.el-scrollbar__view{
  display: inline !important;
}
.main{
  width:100%;
  height:50%;
  background-color: #f3f4f9;

  .query{
    position: relative;
    display: flex;
    align-items: center;
    background-color: #fff;
    height: 15%;
    border-radius: 8px;
    margin-bottom: 20px;

    .input{
      width: 15%;
      height: 60%;
      margin-left: 2%;

      .el-input{
        width: 100%;
        height: 100%;
        font-size: 16px;
      }
    }

    .select{
      width: 15%;
      height: 60%;
      margin-left: 2%;
      margin-top: 5px;

      .el-select{
        width: 100%;
        height: 100%;
        font-size: 16px;
      }
    }

  }

  .table{
    background: #fff;
    border-radius: 8px;
    height: 85%;
  }

  .form{
    background-color: #fff;
    border-radius: 8px;
    margin-bottom: 10px;
    padding: 12px 12px;
    font-size: 16px;
  }
}


</style>