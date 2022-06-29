<template>

    <el-row :gutter="12">
      <el-col
          :key="o"
          :span="8"
      >
        <el-card  shadow="hover" :body-style="{ padding: '0px' } ">
          <img
              src="../../assets/pic_truck.webp"
              class="image"
          />
          <div style="padding: 14px">
            <span>卡车</span>
            <div class="bottom">
              <time class="time">Tue Jun 28 2022    15:41:17 GMT+0800    (中国标准时间)</time>
              <el-button type="primary" :icon="Edit"  >车辆管理</el-button>
            </div>
          </div>
        </el-card>
      </el-col>

    <el-col
        :key="o"
        :span="8"
    >
      <el-card  shadow="hover" :body-style="{ padding: '0px' }">
        <img
            src="../../assets/wa.png"
            class="image"
        />
        <div style="padding: 14px">
          <span>挖掘机</span>
          <div class="bottom">
            <time class="time">Tue Jun 28 2022    15:41:17 GMT+0800    (中国标准时间)</time>
            <el-button type="primary" :icon="Edit" >车辆管理</el-button>
          </div>
        </div>
      </el-card>
    </el-col>

      <el-col
          :key="o"
          :span="8">
        <el-card class="box-card">
          <template #header>
            <div class="card-header">
              <span>车辆统计</span>
              <el-button class="button" text>状态总览</el-button>
            </div>
          </template>
          <div>卡车数量：5</div>
          <div>挖掘机数量：15</div>
          <div>钻机数量：5</div>
          <div>装载机数量：15</div>
          <div>....</div>
          <div>....</div>
        </el-card>
      </el-col>
    </el-row>

  <el-row :gutter="12">
    <el-col
        :key="o"
        :span="8"
    >
      <el-card  shadow="hover" :body-style="{ padding: '0px' } ">
        <img
            src="../../assets/zuanCar.png"
            class="image"
        />
        <div style="padding: 14px">
          <span>钻机</span>
          <div class="bottom">
            <time class="time">Tue Jun 28 2022    15:41:17 GMT+0800    (中国标准时间)</time>
            <el-button type="primary" :icon="Edit"  >车辆管理</el-button>
          </div>
        </div>
      </el-card>
    </el-col>

    <el-col
        :key="o"
        :span="8"
    >
      <el-card  shadow="hover" :body-style="{ padding: '0px' }">
        <img
            src="../../assets/chanCar.png"
            class="image"
        />
        <div style="padding: 14px">
          <span>装载机</span>
          <div class="bottom">
            <time class="time">Tue Jun 28 2022    15:41:17 GMT+0800    (中国标准时间)</time>
            <el-button type="primary" :icon="Edit" >车辆管理</el-button>
          </div>
        </div>
      </el-card>
    </el-col>
  </el-row>
</template>





<script>
export default {
  name: "truckManage"
}
</script>



<style>

.time {
  font-size: 14px;
  color: #999;
  align-items: center;
}

.bottom {
  margin-top: 13px;
  line-height: 12px;
  display: flex;
  justify-content: space-between;
  align-items: center;
}

.button {
  padding: 0;
  min-height: auto;
}

.image {
  width: 100%;
  display: block;
}


.box-card {
  padding: 18px;
  font-size: 24px;
  line-height: 40px;
}
</style>