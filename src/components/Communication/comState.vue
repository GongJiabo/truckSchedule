<template>
  <!-- 数据统计-->
  <div class="etable">
  <el-row :gutter="10">
    <el-col :span="6">
      <div class="statistics" style="background:#409eff" >
        <div class="num"  style="font-size:36px">7</div>
        <div class="tip">人员总数</div>
      </div>
    </el-col>
    <el-col :span="6">
      <div class="statistics" style="background:#E6A23C" >
        <div class="num"  style="font-size:36px">7</div>
        <div class="tip">在线人员数量</div>
      </div>
    </el-col>
  </el-row>
  <el-row :gutter="10">
    <el-col :span="6">
      <div class="statistics" style="background:#67C23A" >
        <div class="num"  style="font-size:36px">7</div>
        <div class="tip">车辆总数</div>
      </div>
    </el-col>
    <el-col :span="6">
      <div class="statistics" style="background:#909399" >
        <div class="num" style="font-size:36px">7</div>
        <div class="tip">工作车辆数量</div>
      </div>
    </el-col>
  </el-row>
  </div>

  <!--为echarts准备一个具备大小的容器dom-->
  <div class="echarts">
    <div id="main" style="width: 800px; height: 600px; margin:auto" ></div>
  </div>

  <div class="table">
    <el-table :data="insertData" border size="large">
      <el-table-column prop="name" label="姓名" min-width="2" />
      <el-table-column prop="phone" label="联系方式" min-width="2" />
      <el-table-column prop="state" label="通讯状态" min-width="2" />
      <el-table-column prop="last" label="上次一在线时间" min-width="3"  />
      <el-table-column fixed="operate" label="操作" min-width="3">
        <template #default>
          <el-button link type="primary" size="small" @click="handleClick">短信编辑</el-button>
          <el-button link type="primary" size="small">历史记录</el-button>
        </template>
      </el-table-column>
    </el-table>
  </div>



</template>

<script setup>
const insertData = [
      {
        name: '张三',
        phone: '123456',
        state: '良好',
        last: '2022-06-08 12:12',
      },
  {
    name: '李四',
    phone: '123456',
    state: '较差',
    last: '2022-06-08 12:12',
  }
    ]

</script>

<script>
import * as echarts from "echarts";

export default {
  name: "comState",
  data() {
    return {
      charts: "",
      opinion: ["在线人员","忙线人员" ,"离线人员"],
      opinionData: [
        //渲染登录与未登录人员数量
        { value: 123, name: "在线人员" },
        { value: 2,   name: "忙线人员" },
        { value: 34, name: "离线人员" },
      ],
    };
  },
  methods: {
    drawPie(id) {
      this.charts = echarts.init(document.getElementById(id));
      this.charts.setOption({
        tooltip: {
          trigger: "item",
        },
        legend: {
          orient: "vertical",
          x: "left",
          data: this.opinion,
        },
        series: [
          {
            name: "登录情况",
            type: "pie",
            radius: ["30%","20%", "50%"],
            avoidLabelOverlap: false,
            label: {
              normal: {
                show: false,
                position: "center",
              },
              emphasis: {
                show: true,
                textStyle: {
                  fontSize: "30",
                  fontWeight: "blod",
                },
              },
            },
            labelLine: {
              normal: {
                show: false,
              },
            },
            data: this.opinionData,
          },
        ],
      });
    },
  },
  //调用
  mounted() {
    this.$nextTick(function () {
      this.drawPie("main");
    });
  },
};

</script>



<style scoped>
* {
  margin: 0;
  padding: 0;
  list-style: none;
}
.el-row {
  margin-bottom: 4px;
}
.etable{
  position: relative;
  left : 25%;
}
.echarts{
  display: flex;
}

.table{
  background: #fff;
  border-radius: 8px;
  height: 85%;
}

</style>