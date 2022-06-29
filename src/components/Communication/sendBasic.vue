<template>
  <el-row>
    <el-col
        v-for="(o, index) in 2"
        :key="o"
        :span="8"
        :offset="index > 0 ? 2 : 0"
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
            <el-button type="primary" :icon="Edit"  >下发基础信息</el-button>
          </div>
        </div>
      </el-card>
    </el-col>
  </el-row>

  <el-col
      v-for="(o, index) in 2"
      :key="o"
      :span="8"
      :offset="index > 0 ? 2 : 0"
  >
    <el-card  shadow="hover" :body-style="{ padding: '0px' }">
      <img
          src="../../assets/wa.png"
          class="image"
      />
      <div style="padding: 14px">
        <span>货车</span>
        <div class="bottom">
          <time class="time">Tue Jun 28 2022    15:41:17 GMT+0800    (中国标准时间)</time>
          <el-button type="primary" :icon="Edit" >下发基础信息</el-button>
        </div>
      </div>
    </el-card>
  </el-col>
</template>


<script>
export default {
  name: "sendBasic"
}
</script>

<style scoped>
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
</style>