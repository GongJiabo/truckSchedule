<template>
  <div style="height: 100%">
    <div class="control_menu" style="height:100%">
      <el-container style="height:100%">
        <el-aside style="height: 100%">
          <el-menu
              active-text-color="#ffd04b"
              background-color="#031022"
              class="el-menu-vertical-demo"
              @open="handleOpen"
              @close="handleClose"
              default-active="1"
              text-color="#fff"
              :default-openeds="['1','2']"
              ref="menu"
              style="height: 100%;"
              router
          >
            <el-sub-menu index="1">
              <template #title>
                <el-icon ><Edit /></el-icon>
                <span>常用命令菜单</span>
              </template>
              <el-menu-item index="/controlMenu/tempSche">临时调度</el-menu-item>
              <el-menu-item index="/controlMenu/upDown">代装代卸</el-menu-item>
              <el-menu-item index="/controlMenu/qiangCom">强制命令</el-menu-item>
              <el-menu-item index="/controlMenu/qiangDu">装卸强度</el-menu-item>
              <el-menu-item index="1-5">强制故障</el-menu-item>
              <el-menu-item index="1-6">装卸量对比</el-menu-item>
              <el-menu-item index="1-7">定铲派车</el-menu-item>
              <el-menu-item index="1-8">铲锁定卸点</el-menu-item>
              <el-menu-item index="1-9">配矿计划</el-menu-item>
            </el-sub-menu>
            <el-sub-menu index="2">
              <template #title>
                <el-icon ><icon-menu /></el-icon>
                <span>数据查询</span>
              </template>
              <el-menu-item index="2-1">系统日志查询</el-menu-item>
              <el-menu-item index="2-2">系统提示信息</el-menu-item>
              <el-menu-item index="2-3">报警提示查询</el-menu-item>
              <el-menu-item index="2-4">产量数据查询</el-menu-item>
              <el-menu-item index="2-5">设备实时状态</el-menu-item>
            </el-sub-menu>
            <el-sub-menu index="3">
              <template #title>
                <el-icon ><document /></el-icon>
                <span>通讯菜单</span>
              </template>
              <!-- jbgong added:-->
              <el-menu-item index="/controlMenu/sendMessage">下发短信</el-menu-item>
              <el-menu-item index="/controlMenu/comState">通讯状态</el-menu-item>
              <el-menu-item index="/controlMenu/sendBasic">下发基础信息</el-menu-item>
              <el-menu-item index="/controlMenu/autoReply">请示自动回复</el-menu-item>
            </el-sub-menu>
            <el-sub-menu index="4">
              <template #title>
                <el-icon ><setting /></el-icon>
                <span>系统维护</span>
              </template>
              <el-menu-item index="/controlMenu/userConfig">用户信息设置</el-menu-item>
              <el-menu-item index="/controlMenu/truckManage">车辆管理</el-menu-item>
            </el-sub-menu>
          </el-menu>
        </el-aside>
        <el-main style="overflow-y: hidden; background-color: #f3f4f9;">
          <router-view/>
        </el-main>
      </el-container>
    </div>
  </div>
</template>

<script>

import {
  Document,
  Menu as IconMenu,
  Edit,
  Setting,
} from '@element-plus/icons-vue'

import * as d3 from 'd3';

export default {
  components:{
    Document,
    IconMenu,
    Edit,
    Setting,
  },
  name: "Menu",
  methods:{
    handleOpen(key, keyPath) {
      // if(key === '3'){
      //   this.$refs.menu.close('1');
      //   this.$refs.menu.close('4');
      //   this.$refs.menu.open('2');
      // }
      // else if(key === '4'){
      //   this.$refs.menu.close('2');
      //   this.$refs.menu.close('1');
      //   this.$refs.menu.open('3')
      // }
      // else if(key === '1'){
      //   this.$refs.menu.open('2');
      //   this.$refs.menu.close('3');
      //   this.$refs.menu.close('4')
      // }
      // else if(key === '2'){
      //   this.$refs.menu.open('1');
      //   this.$refs.menu.close('3');
      //   this.$refs.menu.close('4')
      // }
      console.log(key, keyPath);
    },
    handleClose(key, keyPath) {
      console.log(key, keyPath);
    },
  },
}
</script>

<style scoped>

</style>