<template>
  <div class="mapMain">
    <div class="info">
      <div class="infoHeader">
        <p>卡车调度系统</p>
        <img class="infoHeaderImg" :src="headImg" alt="">
        <div class="item1" @click="twoDClick">
          <p class="titleP">二维显示</p>
          <img :src="kImg1" alt="">
        </div>
        <div class="item2" @click="threeDClick">
          <p class="titleP">三维显示</p>
          <img :src="kImg2" alt="">
        </div>
      </div>
      </div>
    <div class="infoContent">
      <div class="infoContentL">
        <!-- @click.self="big" -->
        <div class="Citem1">
          <img class="bgImg_big" :src="bgImg" alt="">
          <div class="Citem1Content">
            <div class="title">卡车实况</div>
            <div class="carBlock">
              <p>自动调度车辆数：4辆</p>
              <div class="carContent">
                <span>1号车</span>
                <span>2号车</span>
                <span>3号车</span>
                <span>4号车</span>
              </div>
            </div>
            <el-divider class="dash_divider"></el-divider>
            <div class="carBlock" style="margin-top: -20px">
              <p>空车车辆数：3辆</p>
              <div class="carContent">
                <span>5号车</span>
                <span>6号车</span>
                <span>7号车</span>
              </div>
            </div>
            <el-divider class="dash_divider"></el-divider>
            <div class="carBlock" style="margin-top: -20px">
              <p>重车车辆数：2辆</p>
              <div class="carContent">
                <span>8号车</span>
                <span>9号车</span>
              </div>
            </div>
            <el-divider class="dash_divider"></el-divider>
            <div class="carBlock" style="margin-top: -20px">
              <p>作业铲装设备台数：3台</p>
              <div class="carContent">
                <span>设备1</span>
                <span>设备2</span>
                <span>设备3</span>
              </div>
            </div>
          </div>
        </div>
        <div class="Citem2">
          <img class="bgImg_small" :src="bgImg2" alt="">
          <div class="Citem2Content">
            <div class="title">统计分析</div>
            <p>装车车数：174</p>
            <p>卸车车数：160</p>
            <p>装车产量：7300</p>
            <p>卸车产量：7200</p>
          </div>
        </div>
      </div>
      <div class="infoContentM">
        <div class="towD" v-show="is2DShow">
          <div class="row">
            <div class="place">
              <div style="position: absolute;z-index: -1">
                <div style="position: absolute;z-index: -1" id="caichang">
                  <img class="placeImg" :src="bgImg" alt="">
                </div>
                <img class="placeIcon" :src="caiIcon" alt="">
              </div>
              <div style="margin-left: 20px;margin-top: 20px;float: left">
                <el-popover
                    placement="top-start"
                    title="挖掘机"
                    width="400"
                    trigger="hover">
                  <ul class="tips-content">
                    <li>设备编号：挖掘机#1</li>
                    <li>位置：</li>
                    <li>状态：工作中</li>
                  </ul>
                  <template #reference>
                   <img class="carIcon" :src="wacarIcon" alt="">
                  </template>
                </el-popover>
              </div>
              <div style="margin-left: 20px;margin-top: 20px;float: left">
                <img class="carIcon" :src="wacarIcon" alt="">
              </div>
              <div style="margin-left: 10px;margin-top: 20px;float: left">
                <img class="carIcon" :src="chancarIcon" alt="">
              </div>
              <div style="margin-left: 5px;margin-top: 30px;float: left">
                <img class="carIcon" :src="zuancarIcon" alt="">
              </div>
              <div style="margin-left: 5px;margin-top: 30px;float: left">
                <img class="carIcon" :src="zuancarIcon" alt="">
              </div>
            </div>
<!--            <div class="road">-->

<!--            </div>-->
<!--            <div class="road">-->

<!--            </div>-->
            <div class="place" style="margin-left: 450px">
            <div style="position: absolute;z-index: -1">
              <div style="position: absolute;z-index: -1" id="xiulichang">
                <img class="placeImg" :src="bgImg" alt="">
              </div>
              <img class="placeIcon" :src="xiuIcon" alt="">
            </div>
              <div style="margin-left: 40px;margin-top: 20px;float: left">
                <img class="carIcon" :src="wacarIcon" alt="">
              </div>
              <div style="margin-left: 40px;margin-top: 40px;float: left">
                <img class="carIcon" :src="cacarIcon" alt="">
              </div>
              </div>
          </div>
          <div class="row" style="margin-top: 50px;justify-content: center;">
            <div class="place">
              <div style="position: absolute;z-index: -1">
              <div style="position: absolute;z-index: -1" id="posuizhan">
                <img class="placeImg" :src="bgImg" alt="">
              </div>
              <img class="placeIcon" :src="poIcon" alt="">
                </div>
              <div style="margin-left: 30px;margin-top: 30px;float: left">
                <img class="carIcon" :src="wacarIcon" alt="">
              </div>
              <div style="margin-left: 20px;margin-top: 20px;float: left">
                <img class="carIcon" :src="wacarIcon" alt="">
              </div>
              <div style="margin-left: 20px;margin-top: 40px;float: left">
                <img class="carIcon" :src="chancarIcon" alt="">
              </div>
            </div>
          </div>
          <div class="row" style="margin-top: 50px">
            <div class="place">
              <div style="position: absolute;z-index: -1">
              <div style="position: absolute;z-index: -1" id="tingchechang">
                <img class="placeImg" :src="bgImg" alt="">
              </div>
              <img class="placeIcon" :src="pIcon" alt="">
                </div>
              <div style="margin-left: 20px;margin-top: 20px;float: left">
                <img class="carIcon" :src="wacarIcon" alt="">
              </div>
              <div style="margin-left: 20px;margin-top: 20px;float: left">
                <img class="carIcon" :src="cacarIcon" alt="">
              </div>
              <div style="margin-left: 20px;margin-top: 20px;float: left">
                <img class="carIcon" :src="cacarIcon" alt="">
              </div>
              <div style="margin-left: 20px;margin-top: 20px;float: left">
                <img class="carIcon" :src="cacarIcon" alt="">
              </div>
            </div>
<!--            <div class="road">-->

<!--            </div>-->
            <div class="place" style="margin-left: 450px">
              <div style="position: absolute;z-index: -1">
              <div style="position: absolute;z-index: -1" id="youguan">
                <img class="placeImg" :src="bgImg" alt="">
              </div>
              <img class="placeIcon" :src="youIcon" alt="">
                </div>
              <div style="margin-left: 20px;margin-top: 20px;float: left">
                <img class="carIcon" :src="wacarIcon" alt="">
              </div>
              <div style="margin-left: 10px;margin-top: 10px;float: left">
                <img class="carIcon" :src="youcarIcon" alt="">
              </div>
              <div style="margin-left: 30px;margin-top: 30px;float: left">
                <img class="carIcon" :src="youcarIcon" alt="">
              </div>
            </div>
          </div>
        </div>

        <div class="threeD" v-show="is3DShow">
          <img class="3D_main" :src="threeD_model" alt="">
        </div>
      </div>
      <div class="infoContentR">
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
            <!--            <el-sub-menu index="1-6">-->
            <!--              <template #title>item four</template>-->
            <!--              <el-menu-item index="1-4-1">item one</el-menu-item>-->
            <!--            </el-sub-menu>-->
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

            <!--jbgong added:-->
            <el-menu-item index="/controlMenu/sendMessage">下发短信</el-menu-item>
            <el-menu-item index=“/controlMenu/comState>通讯状态</el-menu-item>
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
      </div>
    </div>
      <img v-for='(item) in iconList' class="picGen"  :key="item.id" :src="item.type"  alt=""  :style="{ left: item.left + 'px', top: item.top + 'px' }">
  </div>
</template>


<script>
import LeaderLine from "leader-line-vue";
import * as d3 from 'd3';
// import { getCurrentInstance } from 'vue'
import {
  Document,
  Menu as IconMenu,
  Edit,
  Setting,
} from '@element-plus/icons-vue'

export default{
  components:{
    Document,
    IconMenu,
    Edit,
    Setting,
  },
  data() {
    return{
      headImg:require('@/assets/head_middle.png'),
      kImg1:require('@/assets/head_left.png'),
      kImg2:require('@/assets/head_right.png'),
      bgImg: require('@/assets/bg2.png'),
      bgImg2: require('@/assets/bg.png'),
      caiIcon: require('@/assets/cai.svg'),
      youIcon: require('@/assets/you.svg'),
      pIcon:require('@/assets/p.svg'),
      poIcon:require('@/assets/po.svg'),
      xiuIcon:require('@/assets/xiu.svg'),
      wacarIcon:require('@/assets/wa.png'),
      youcarIcon:require('@/assets/youCar.png'),
      chancarIcon:require('@/assets/chanCar.png'),
      zuancarIcon:require('@/assets/zuanCar.png'),
      cacarIcon:require('@/assets/caCar.png'),
      threeD_model:require('@/assets/3D_main.png'),
      iconList:[],
      is2DShow:true,
      is3DShow:false,
    }
  },
  methods:{
    handleOpen(key, keyPath) {
      if(key === '3'){
        this.$refs.menu.close('1');
        this.$refs.menu.close('4');
        this.$refs.menu.open('2');
      }
      else if(key === '4'){
        this.$refs.menu.close('2');
        this.$refs.menu.close('1');
        this.$refs.menu.open('3')
      }
      else if(key === '1'){
        this.$refs.menu.open('2');
        this.$refs.menu.close('3');
        this.$refs.menu.close('4')
      }
      else if(key === '2'){
        this.$refs.menu.open('1');
        this.$refs.menu.close('3');
        this.$refs.menu.close('4')
      }
    },
    handleClose(key, keyPath) {
      console.log(key, keyPath);
    },
    twoDClick(){
      location.reload()
    },
    threeDClick(){
      d3.selectAll('.leader-line').remove();
      d3.selectAll('.picGen').remove();
      let that = this;
      that.is2DShow = false;
      that.is3DShow = true;
    },
    drawLine(){
      d3.selectAll('.leader-line').remove();
      d3.selectAll('.picGen').remove();
      let caiEle = document.getElementById('caichang');
      let poEle = document.getElementById('posuizhan');
      let pEle = document.getElementById('tingchechang');
      let xiuEle = document.getElementById('xiulichang');
      let youEle = document.getElementById('youguan');
      console.log(caiEle);
      LeaderLine.setLine(caiEle, poEle, {
        dash: {
          animation: true,
          gap: 12
        },
        path:'straight',
        endPlug:'behind',
      });
      LeaderLine.setLine(caiEle, xiuEle,{
        dash: {
          animation: true,
          gap: 12
        },
        path:'straight',
        endPlug:'behind',
        middleLabel: LeaderLine.obj.captionLabel('1'),
      });
      LeaderLine.setLine(caiEle, pEle,{
        dash: {
          animation: true,
          gap: 12
        },
        path:'straight',
        endPlug:'behind'
      });
      LeaderLine.setLine(pEle, youEle, {
        dash: {
          animation: true,
          gap: 12
        },
        endPlug:'behind',
        path:'straight',
      });
      LeaderLine.setLine(xiuEle, youEle, {
        dash: {
          animation: true,
          gap: 12,
        },
        endPlug:'behind',
        path:'straight',
      });
      LeaderLine.setLine(pEle, poEle, {
        dash: {
          animation: true,
          gap: 12
        },
        endPlug:'behind',
        path:'straight',
        middleLabel: LeaderLine.obj.captionLabel('2'),
      });
      LeaderLine.setLine(poEle, youEle, {
        dash: {
          animation: true,
          gap: 12
        },
        endPlug:'behind',
        path:'straight',
        middleLabel: LeaderLine.obj.captionLabel('1'),
      });
      LeaderLine.setLine(xiuEle, poEle, {
        dash: {
          animation: true,
          gap: 12
        },
        endPlug:'behind',
        path:'straight',
      });

    },

    drawIcon(){
      console.log(1);
      let that = this;
      that.iconList = [];
      var id = 0;
      d3.selectAll("svg").select("text").each(function(d, i, node)  {
        let onePoint = {};
        let left = parseFloat(d3.select(this).attr("x").split("px")[0]) - 30;
        onePoint["left"] = left;
        let top = parseFloat(d3.select(this).attr("y").split("px")[0]) - 30;
        onePoint["top"] = top;
        if(d3.select(this)._groups[0][0].innerHTML === "1"){
          d3.select(this)._groups[0][0].innerHTML = '';
          onePoint["type"] = "/static/wa.png";
        }
        else if(d3.select(this)._groups[0][0].innerHTML === "2"){
          d3.select(this)._groups[0][0].innerHTML = '';
          onePoint["type"] = "/static/youCar.png";
        }
        onePoint['id'] = id;
        that.iconList.push(onePoint);
        id++;
      });
      console.log(that.iconList)
    },

  },

  mounted() {
    this.drawLine();
    this.drawIcon();
  },
  watch: {
    $route(to, from) {
      if (to.path !== "/") {
        d3.selectAll('.leader-line').remove();
        d3.selectAll('.picGen').remove();
      }
    }
  }
}

</script>

<style lang='scss'>

.picGen{
  position: absolute;
  height: 50px;
  width: 70px;
}


.bgImg_big {
  position: absolute;
  width: 100% !important;
  height: 500px;
  left: 0;
  z-index: -1;
}

.bgImg_small {
  position: absolute;
  width: 100% !important;
  height: 300px;
  left: 0;
  z-index: -1;
}

.mapMain {
  width: 100%;
  height: 100%;
  position: fixed;
  top: 0;
  right: 0;
  bottom: 0;
  left: 0;
  background-image: linear-gradient(rgba(3, 16, 41, 1) 100%, rgba(255, 255, 255, 0.001) 99%);

  .infoHeader {
    position: relative;
    background-image: linear-gradient(rgba(3, 16, 41, 1) 80%, rgba(255, 255, 255, 0.001) 99%);
    height: 100px;

    p {
      color: #01CEFB;
      font-size: 28px;
      margin-top: 21px;
    }

    .infoHeaderImg {
      position: absolute;
      top: 24px;
      height: 55%;
      right: 50%;
      transform: translateX(50%)
    }

    .item1,
    .item2 {
      position: absolute;
      top: 29px;
      height: 55%;
      right: 65%;
      transform: translateX(50%);
      width: 8.5%;
      cursor: pointer;

      img {
        height: 100%;
        width: 100%;
      }

      p {
        position: absolute;
        margin: 0;
        font-size: 18px;
        width: 100%;
        color: #FFD200;
        right: 50%;
        line-height: 55px;
        transform: translateX(50%);
      }
    }

    .item2 {
      top: 29px;
      right: 35%;

      p {
        color: #009CFF;
      }
    }
  }

  .infoContent {

    .infoContentL,
    .infoContentR {
      position: fixed;
      width: 20%;
      height: 100%;
      background-image: linear-gradient(to right, #031029 30%, rgba(3, 16, 43, 0.7) 90%, rgba(24, 53, 83, 0.01) 100%);
      top: 0;
      margin-top: 20px;

      .Citem1 {
        .Citem1Content {
          display: inline-block;
          float: left;
          width: 100%;
          height: 100%;

          .title{
            color: #496174;
            float: left;
            font-size: 28px;
            font-weight: bold;
            width: 100%;
          }

          .dash_divider{
            border-top: 1px dashed #e8eaec;
            width: 80%;
            margin-bottom: 0 !important;
            margin-top: 0 !important;
          }
        }
      }

      .Citem1
      {
        width: 402px;
        margin-left: 21px;
        margin-right: 21px;
        height: 500px;
        text-align: left;

        .carBlock{
          height: 23%;
          width:100%;
          p {
            color: #fff;
            font-size: 20px;
            height: 20px;
          }


          .carContent{
            float:left;

            span{
              width: 100%;
              color: #fff;
              font-size: 16px;
              line-height: 18px;
              display:block;
            }
          }

        }


        .border {
          box-sizing: border-box;
          width: 402px;
          height: 1px;
          background: #444F5D;
          border-left: #009CFF solid 30px;
          margin-bottom: 30px;
        }

        img {
          float: right;
          width: 40px;
        }
      }
      .Citem2{
        width: 402px;
        margin-left: 21px;
        margin-right: 21px;
        height: 270px;
        text-align: left;

        .title{
          color: #496174;
          float: left;
          font-size: 28px;
          font-weight: bold;
          width: 100%;
        }

        p {
          color: #fff;
          margin-bottom: 15px;
          margin-top: 20px;
          padding-top: 30px;
          font-size: 16px;
        }

        .border {
          box-sizing: border-box;
          width: 402px;
          height: 1px;
          background: #444F5D;
          border-left: #009CFF solid 30px;
          margin-bottom: 30px;
        }

        img {
          float: right;
          width: 40px;
        }
      }
    }

    .infoContentL {

      .itemSwitch {
        float: right;
        font-size: 16px;

        p {
          cursor: pointer;
        }

        p:first-child {
          color: #009CFF;
        }

        img {
          margin: 0 5px;
          width: 14px;
          float: none;
        }
      }
    }

    .infoContentR {
      background-image: linear-gradient(to left, #031029 30%, rgba(3, 16, 43, 0.7) 90%, rgba(24, 53, 83, 0.01) 100%);
      right: 0;

      .Citem1 {
        height: 350px;
        margin-bottom: 70px;
      }

      .itemSwitch {
        float: right;
        font-size: 16px;

        p {
          cursor: pointer;
        }

        p:first-child {
          color: #009CFF;
        }

        img {
          margin: 0 5px;
          width: 14px;
          float: none;
        }
      }
    }

    .infoContentM{
      position: fixed;
      width: 60%;
      margin-left: 23%;
      height: 100%;
      top: 0;
      margin-top: 100px;

      .towD{
        height: 90%;
        width: 90%;
        margin-top: 5%;
        margin-left: 5%;
        .row{
          width: 100%;
          height: 220px;
          display: flex;
          .place{
            height: 200px;
            width: 280px;
            .carIcon{
              height: 50px;
              width: 80px;
              z-index: 3;
            }
            .placeImg{
              height: 200px;
              width: 250px;
              z-index: 2;
            }
            .placeIcon{
              height: 175px;
              width: 240px;
              z-index: 1;
              opacity: 0.25;
              margin-top: 18px;
              //margin-left: -10px;
            }
          }
          .road{
            margin-top: 50px;
            height: 80px;
            width: 220px;
            background-color: white;
          }
          .roadVer{
            height: 100px;
            width: 80px;
          }
        }
      }

      .threeD{
        height: 100%;
        width: 100%;

        img{
          height:90%;
          width: 100%;
        }
      }
    }
  }

}
</style>