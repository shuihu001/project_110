<template>
  <div>

    <div class="card1 bbxx" style="width: 100%">
      <div class="chartUser">

        <el-form :model="declareForm" status-icon label-width="30px" class="demo-ruleForm" style="padding-right: 30px" enctype='multipart/form-data'>
          <div class="helpinfo">
            <p><span class="wrtext">本申报适用于已加入展会计划的申报！</span></p>
            <p><font class="hptext">请认真填写展会活动登记表，提交后未经审核无法修改</font></p>
          </div>

          <div style="padding: 18px; transform: translateY(20%)">
            <label class="kindsfont">一、基础信息</label>
          </div>
          <el-form-item style="margin-top: 20px">
            <label class="xrequired">展会名称</label>
            <el-input type="text" ref="name" v-model="declareForm.name" auto-complete="off"
                      placeholder=""></el-input>
          </el-form-item>
          <el-form-item>
            <label class="xrequired">主办单位</label>
            <el-input type="text" ref="hostComp" v-model="declareForm.hostComp" auto-complete="off"
                      placeholder=""></el-input>
          </el-form-item>
          <el-form-item>
            <label class="xrequired">承办单位</label>
            <el-input type="text" ref="fundComp" v-model="declareForm.fundComp" auto-complete="off"
                      placeholder=""></el-input>
          </el-form-item>
          <el-form-item>
            <label>协办单位</label>
            <el-input type="text" ref="supportComp" v-model="declareForm.supportComp" auto-complete="off"
                      placeholder=""></el-input>
          </el-form-item>
          <el-form-item>
            <label>指导单位</label>
            <el-input type="text" ref="orderComp" v-model="declareForm.orderComp" auto-complete="off"
                      placeholder=""></el-input>
          </el-form-item>
          <div style="padding: 18px">
            <label class="kindsfont">二、办展依据</label>
          </div>
          <div class="attention">
            <p><font class="hptext">注：省部主办展会须提供全国清理和规范庆典研讨会论坛活动工作领导小组的批文；事业单位主办展会须提供行业主管司局审核意见；境外组团参展须提供国际合作司审核意见</font></p>
          </div>
          <el-row :gutter="0">
            <el-col :span="12">
              <el-form-item>
                <label class="xrequired">批准单位</label>
                <el-input type="text" ref="authObj" v-model="declareForm.authObj" auto-complete="off"
                          placeholder=""></el-input>
              </el-form-item>
            </el-col>
            <el-col :span="12">
              <el-form-item>
                <label>批准文号（选填）</label>
                <el-input type="text" ref="authNum" v-model="declareForm.authNum" auto-complete="off"
                          placeholder=""></el-input>
              </el-form-item>
            </el-col>
          </el-row>
					<el-form-item enctype="multipart/form-data">
						<div class="authorizeFile">
							<label class="xrequired">去年审批文件</label><br />
							<input type="file" ref="authorizeFile"
              accept=".pdf" name="authorizeFile"></input>
						</div>

					</el-form-item>
          <div style="padding: 18px">
            <label class="kindsfont">三、举办计划</label>
          </div>

          <el-row :gutter="0">
            <el-col :span="17">
              <el-form-item>
                <label class="xrequired">举办地点&举办时间</label>
                <choose-city ref='chooseCity' :cityData = 'this.chooseCityTag'></choose-city>
                <el-input type="text" ref="place" v-model="declareForm.place" auto-complete="off"
                          placeholder="具体举办地点，如xx展览中心"></el-input>
              </el-form-item>
            </el-col>
            <el-col :span="10">
                <el-date-picker
                  ref="Times"
                  v-model="declareForm.Times"
                  type="datetimerange"
                  size = 'large'
                  style="margin-top:44px"
                  start-placeholder="开始日期"
                  end-placeholder="结束日期"
                  value-format="yyyy-MM-dd HH:mm:ss"
                  :default-time="['8:00:00', '18:00:00']">
                </el-date-picker>
              </el-col>
            <!-- <el-col :span="7">
              <el-form-item>
                <label>开始时间</label>
                <el-input type="date" ref="beginTime" name="beginTime" v-model="declareForm.beginTime" auto-complete="off"
                          placeholder=""></el-input>
              </el-form-item>
            </el-col>
            <p class="timeMid">——</p>
            <el-col :span="7">
              <el-form-item>
                <label>结束时间</label>
                <el-input type="date" ref="endTime" name="endTime" v-model="declareForm.endTime" auto-complete="off"
                          placeholder=""></el-input>
              </el-form-item>
            </el-col> -->
          </el-row>

          <el-row>
            <el-col :span="12">
              <el-form-item>
                <label  class="xrequired">展览面积（m²）</label>
                <el-input type="number" ref="area" v-model="declareForm.area" auto-complete="off"
                          placeholder=""></el-input>
              </el-form-item>
            </el-col>
          </el-row>



          <el-form-item>
            <label  class="xrequired">展会基本情况(100字以内)</label>
            <el-input type="textarea" ref="meetState" :maxlength="100" v-model="declareForm.meetState" auto-complete="off"
                      placeholder="主题、主要内容、展区规划等"></el-input>
          </el-form-item>
          <el-form-item>
            <label  class="xrequired">同期活动(200字以内)</label>
            <el-input type="textarea" ref="activityBrief" :maxlength="200" v-model="declareForm.activityBrief" auto-complete="off"
                      placeholder=""></el-input>
          </el-form-item>
          <el-row :gutter="0">
            <el-col :span="12">
              <el-form-item>
                <p><label>是否邀请境外有关机构及参展商</label>
                     <input style="vertical-align:middle;" ref="foreign" type="checkbox" v-model="declareForm.foreign" name="views" auto-complete="off"
                             placeholder=""></input>
                </p>

              </el-form-item>
            </el-col>
            <el-col :span="12">
              <el-form-item>
                <p><label  class="xrequired">观众构成</label></p>
                <el-row :gutter="0">
                  <el-col :span="2">
                    <div><br></div>
                  </el-col>
                  <el-col :span="12">
                    <p style="font-size: 10px">
                      <label style="vertical-align:middle;">是否有采购商参加</label>

                     <input style="vertical-align:middle;" ref="view1" type="checkbox" v-model="declareForm.view1" name="views" auto-complete="off"
                             placeholder=""></input>
                    </p>
                  </el-col>
                  <el-col :span="8">
                    <p style="font-size: 10px">
                      <label style="vertical-align:middle;">是否有消费者参加</label>
                      <input style="vertical-align:middle;" ref="view2" type="checkbox" v-model="declareForm.view2" name="views" auto-complete="off"
                             placeholder=""></input>
                    </p>
                  </el-col>
                </el-row>
              </el-form-item>
            </el-col>
          </el-row>

          <div style="padding: 18px">
            <label class="kindsfont xrequired" >四、经费来源</label>
          </div>

          <el-form-item>
            <label>财政金额（万元）</label>
            <el-input type="number" ref="finanFund" v-model="declareForm.finanFund" auto-complete="off"
            oninput="if(value.length > 8) value = value.slice(0,8)"
                      placeholder=""></el-input>
            <label>自筹金额（万元）</label>
            <el-input type="number" ref="selfFund" v-model="declareForm.selfFund" auto-complete="off"
            oninput="if(value.length > 8) value = value.slice(0,8)"
                      placeholder=""></el-input>
          </el-form-item>


          <div style="padding: 18px">
            <label class="kindsfont">五、拟邀请领导情况</label>
          </div>

          <el-form-item>
            <p><label>领导出席情况</label></p>
            <el-col :span="12">
              <p style="font-size: 10px">
                <label style="vertical-align:middle;">党和国家领导人</label>
                <input style="vertical-align:middle;" ref="leaderN" type="checkbox" v-model="declareForm.leaderN" name="leaderN" auto-complete="off"
                       placeholder=""></input>
              </p>
            </el-col>
            <el-col :span="12">
              <p style="font-size: 10px">
                <label style="vertical-align:middle;">有关司局和事业单位负责人</label>
                <input style="vertical-align:middle;" ref="leaderD" type="checkbox" v-model="declareForm.leaderD" name="leaderD" auto-complete="off"
                       placeholder=""></input>
              </p>
            </el-col>
            <el-col :span="12">
              <p style="font-size: 10px">
                <label style="vertical-align:middle;">省部级以上领导</label>
                <input style="vertical-align:middle;" ref="leaderP" type="checkbox" v-model="declareForm.leaderP" name="leaderP" auto-complete="off"
                       placeholder=""></input>
              </p>
            </el-col>
            <el-col :span="12">
              <p style="font-size: 10px">
                <label style="vertical-align:middle;">国家级行业协会负责人</label>
                <input style="vertical-align:middle;" ref="leaderA" type="checkbox" v-model="declareForm.leaderA" name="leaderA" auto-complete="off"
                       placeholder=""></input>
              </p>
            </el-col>
            <el-col :span="12">
              <p style="font-size: 10px">
                <label style="vertical-align:middle;">是否有国外政府官员含驻华使馆</label>
                <input style="vertical-align:middle;" ref="leaderF" type="checkbox" v-model="declareForm.leaderF" name="leaderF" auto-complete="off"
                       placeholder=""></input>
              </p>
            </el-col>
          </el-form-item>

          <div style="padding: 18px">
            <label class="kindsfont xrequired">六、填报单位信息</label>
          </div>

          <el-form-item>
            <label class="xrequired">填报单位</label>
            <el-input type="text" ref="writeObject" v-model="declareForm.writeObject" auto-complete="off"></el-input>
            <label class="xrequired">责任处室</label>
            <el-input type="text" ref="department" v-model="declareForm.department" auto-complete="off"></el-input>
            <label class="xrequired">处室负责人</label>
            <el-input type="text" ref="charger" v-model="declareForm.charger" auto-complete="off"></el-input>
            <label class="xrequired">负责人手机号</label>
            <el-input type="number" ref="teleNum" v-model="declareForm.teleNum" auto-complete="off"
            oninput="if(value.length > 11) value = value.slice(0,11)"></el-input>
          </el-form-item>

					<el-form-item enctype="multipart/form-data">
          <div class="filePlc">
						<div class="inputFile1">
							<label class="xrequired">展会工作方案</label><br />
							<input type="file" ref="inputFile1"
              accept=".pdf" name="preExpoFile"></input>
						</div>

						<div class="inputFile2">
							<label class="xrequired">招展招商方案</label><br/>
							<input type="file" ref="inputFile2"  accept=".pdf" name="investmentPlanFile"></input>
						</div>
          </div>


					</el-form-item>
              <!-- <form enctype='multipart/form-data' action="http://192.168.1.101:8445/api/handin/detail" method="post" target="#">
                <input type="file" name='preExpoFile' accept=".pdf"  ref="inputFile1">
                <input type="file" name='investmentPlanFile' accept=".pdf"  ref="inputFile2">
                <input type="submit">
              </form >   -->

          <el-form-item style="padding-bottom:30px; padding-right: 30px" enctype='multipart/form-data'>

            <el-button class="subBtn" type="primary" v-on:click="declareFormed">提交</el-button>
          </el-form-item>

        </el-form>

      </div>
    </div>


  </div>
</template>

<script>
import { getEasy } from "../../network/getForm";
import { getDetail } from "../../network/getForm";

import chooseCity from "../../components/common/chooseCity/chooseCity";
export default {
  name: "easyfont",
  data() {
    return {
      chooseCityTag: "",
      declareForm: {
        name: "",
        hostComp: "",
        fundComp: "",
        guideComp: "",
        supportComp: "",
        authObj: "",
        authNum: "",
        place: "",
        Times: [],
        cycle: "",
        area: "",
        meetState: "",
        activityBrief: "",
        foreign: false,
        view1: false,
        view2: false,
        willInvite: "",
        capitalSource: "",
        finanfrom: "",
        orderComp: "",
        finanFund: "",
        selfFund: "",
        //填报单位
        writeObject: "",
        //负责处室
        department: "",
        //处室负责人
        charger: "",
        //手机号
        teleNum: "",
        //党和国家领导人
        leaderN: false,
        //有关司局和事业单位负责人
        leaderD: false,
        //省部级以上领导
        leaderP: false,
        // 国家级行业协会负责人
        leaderA: false,
        // 是否有国外政府官员含驻华使馆
        leaderF: false,
        
        
        
      },
    };
  },
  components: {
    chooseCity,
  },
  created() {
    getEasy(this.$store.getters.token).then((res) => {
      console.log(res.data)
      if (res.data) {
        if (!res.data.summaryDone & res.data.checkState == 2) {
          alert("请先完成上报总结");
          this.$router.push("handin");
        }
        (this.declareForm = res.data),
          (this.declareForm.leaderN = parseInt(res.data.leaderState.slice(0,1))),
          (this.declareForm.leaderD = parseInt(
            res.data.leaderState.slice(1,2)
          )),
          (this.declareForm.leaderP = parseInt(
            res.data.leaderState.slice(2,3)
          )),
          (this.declareForm.leaderA = parseInt(
            res.data.leaderState.slice(3,4)
          )),
          (this.declareForm.leaderF = parseInt(res.data.leaderState.slice(4,5)),
          (this.declareForm.Times = [res.data.startTime, res.data.endTime]),
          (this.chooseCityTag = res.data.chooseCity);
        console.log(this.declareForm);
      } else {
        getDetail(this.$store.getters.token).then((res) => {
          if (res.data) {
            if (!res.data.summaryDone & res.data.checkState == 2) {
              alert("请先完成上报总结");
              this.$router.push("handin");
            }
            (this.declareForm = res.data),
              (this.declareForm.leaderN = parseInt(
                res.data.leaderState / 10000
              )),
              (this.declareForm.leaderD = parseInt(
                (res.data.leaderState % 10000) / 10
              )),
              (this.declareForm.leaderP = parseInt(
                (res.data.leaderState % 1000) / 10
              )),
              (this.declareForm.leaderA = parseInt(
                (res.data.leaderState % 100) / 10
              )),
              (this.declareForm.leaderF = parseInt(res.data.leaderState % 10)),
              (this.declareForm.Times = [res.data.startTime, res.data.endTime]),
              console.log(this.declareForm);
          }
        });
      }
    });
  },
  computed: {
    leaderPresent() {
      return (
        (this.declareForm.leaderN & 1).toString() +
        (this.declareForm.leaderD & 1).toString() +
        (this.declareForm.leaderP & 1).toString() +
        (this.declareForm.leaderA & 1).toString() +
        (this.declareForm.leaderF & 1).toString()
      );
    },
  },
  methods: {
    declareFormed() {
      if (!this.declareForm.name) {
        this.$message({
          showClose: true,
          message: "请填写展会名称！",
          type: "error",
        });
        this.$refs.name.focus();
        return false;
      }
      if (!this.declareForm.hostComp) {
        this.$message({
          showClose: true,
          message: "请填写展会主办单位！",
          type: "error",
        });
        this.$refs.hostComp.focus();
        return false;
      }
      if (!this.declareForm.fundComp) {
        this.$message({
          showClose: true,
          message: "请填写承办单位！",
          type: "error",
        });
        this.$refs.fundComp.focus();
        return false;
      }
      if (!this.declareForm.authObj) {
        this.$message({
          showClose: true,
          message: "请填写批准单位！",
          type: "error",
        });
        this.$refs.authObj.focus();
        return false;
      }

      if (!this.declareForm.place) {
        this.$message({
          showClose: true,
          message: "举办地点！",
          type: "error",
        });
        this.$refs.place.focus();
        return false;
      }
      if (!this.declareForm.Times[0]) {
        this.$message({
          showClose: true,
          message: "请填写举办时间！",
          type: "error",
        });
        this.$refs.Times.focus();
        return false;
      }
      if (!this.declareForm.area) {
        this.$message({
          showClose: true,
          message: "请填写举办面积！",
          type: "error",
        });
        this.$refs.area.focus();
        return false;
      }
      if (!this.declareForm.meetState) {
        this.$message({
          showClose: true,
          message: "请填写展会基本情况！",
          type: "error",
        });
        this.$refs.meetState.focus();
        return false;
      }

      if (!this.declareForm.activityBrief) {
        this.$message({
          showClose: true,
          message: "请填写同期活动！",
          type: "error",
        });
        this.$refs.activityBrief.focus();
        return false;
      }
      if (!(this.declareForm.view1 || this.declareForm.view2)) {
        this.$message({
          showClose: true,
          message: "请填写观众构成！",
          type: "error",
        });
        this.$refs.view1.focus();
        return false;
      }
      if (!(this.declareForm.finanFund || this.declareForm.selfFund)) {
        this.$message({
          showClose: true,
          message: "请填写经费来源！",
          type: "error",
        });
        this.$refs.finanFund.focus();
        return false;
      }
      let ip0 = this.$refs.authorizeFile;
      let ip1 = this.$refs.inputFile1;
      let ip2 = this.$refs.inputFile2;
      var formdata = new FormData();
      if (!ip0.files[0]) {
        this.$message({
          showClose: true,
          message: "请填写去年审批文件！",
          type: "error",
        });
        this.$refs.authorizeFile.focus();
        return false;
      }
      if (!ip1.files[0]) {
        this.$message({
          showClose: true,
          message: "请填写展会工作方案！",
          type: "error",
        });
        this.$refs.inputFile1.focus();
        return false;
      }
      if (!ip2.files[0]) {
        this.$message({
          showClose: true,
          message: "请填写招展招商方案！",
          type: "error",
        });
        this.$refs.inputFile2.focus();
        return false;
      }
      //展会简称
      formdata.append("meetAddr", this.$store.getters.token);
      // 财政资金的拨款金额
      formdata.append("finanFund", this.declareForm.finanFund);
      // 其他来源的拨款金额
      // formdata.append("otherFund", this.declareForm.otherfond);
      // 展会面积
      formdata.append("area", this.declareForm.area);
      // 是否邀请国外参展商
      formdata.append("foreign", this.declareForm.foreign);
      // 展会名称
      formdata.append("name", this.declareForm.name);
      // 主办单位
      formdata.append("hostComp", this.declareForm.hostComp);
      // 承办单位
      formdata.append("fundComp", this.declareForm.fundComp);
      // 协办单位
      formdata.append("supportComp", this.declareForm.supportComp);
      // 指导单位
      formdata.append("orderComp", this.declareForm.orderComp);
      // 批准单位
      formdata.append("authObj", this.declareForm.authObj);
      // 批准文案
      formdata.append("authNum", this.declareForm.authNum);
      // 举办城市
      formdata.append("chooseCity", this.$refs.chooseCity.getChoosedCity());
      // 举办场所
      formdata.append("place", this.declareForm.place);
      // 举办周期
      formdata.append("cycle", this.declareForm.cycle);
      //开始时间
      formdata.append("startTime", this.declareForm.Times[0]);
      //结束时间
      formdata.append("endTime", this.declareForm.Times[1]);
      // 展会内容
      formdata.append("meetState", this.declareForm.meetState);
      // 财政资金数额
      formdata.append("finanFund", this.declareForm.finanFund);
      // 自筹资金数额
      formdata.append("selfFund", this.declareForm.selfFund);
      //出席领导情况
      formdata.append("leaderState", this.leaderPresent);
      //同期活动
      formdata.append("activityBrief", this.declareForm.activityBrief);
      //填报单位
      formdata.append("writeObject", this.declareForm.writeObject);
      //负责处室
      formdata.append("department", this.declareForm.department);
      //处室负责人
      formdata.append("charger", this.declareForm.charger);
      //手机号
      formdata.append("teleNum", this.declareForm.teleNum);
      //展会工作方案文档
      formdata.append("meetPlanFile", ip1.files[0]);
      //招展招商方案文档
      formdata.append("investmentPlanFile", ip2.files[0]);
      //上级单位审核意见
      formdata.append("authFile", ip0.files[0]);
      //是否采购商参加
      formdata.append("view1", this.declareForm.view1);
      //是否消费者参加
      formdata.append("view2", this.declareForm.view2);
      console.log(this.leaderPresent);
      // console.log(formdata);
      // console.log(formdata.get("finanFrom"));

      // sendEasy(formdata)
      //   .then((successResponse) => {
      //     if (successResponse.data.code === 0) {
      //       this.$router.push("/").catch(() => {});
      //     } else {
      //       this.$message({
      //         showClose: true,
      //         message: "提交失败！",
      //         type: "error",
      //       });
      //     }
      //   })
      //   .catch((failResponse) => {});

      var axios = require("axios");
      axios
        .post("http://8.131.56.110:8445/api/handin/easy", formdata)
        .then((successResponse) => {
          if (successResponse.data.code === 0) {
            this.$router.push("/").catch(() => {});
          } else {
            this.$message({
              showClose: true,
              message: "提交失败！",
              type: "error",
            });
          }
        })
        .catch((failResponse) => {});
    },
  },
};
</script>

<style lang="scss">
$top: top;
$bottom: bottom;
$left: left;
$right: right;
$leftright: ($left, $right);
$pinkk: #eec2d3;
$bluee: #409eff;
$yelloww: #f4d884;
$grennn: #89dda0;
$purplee: #78a2ea;
$lightBluee: #b8d6ff;

$list: bluee pinkk yelloww grennn purplee lightBluee;
$list1: $bluee $pinkk $yelloww $grennn $purplee $lightBluee;
%shadow {
  background: #fff;
  -webkit-box-shadow: 4px 4px 40px rgba(0, 0, 0, 0.2);
  box-shadow: 4px 4px 40px rgba(0, 0, 0, 0.2);
  border-color: rgba(0, 0, 0, 0.2);
  .title {
    font-size: 14px;
    padding: 10px;
    i {
      margin-#{$right}: 5px;
    }
  }
}

@mixin flex($direction: row, $content: space-between) {
  display: flex;
  flex-direction: $direction;
  justify-content: $content;
}

.kindsfont {
  font-size: 20px;
  font-family: 华文细黑;
}

.helpinfo {
  background-color: rgba(70, 130, 180, 0.1);
  transform: translateY(24%);
  margin: 10px;
  padding: 10px;
  width: 556px;
}
.attention {
  background-color: rgba(70, 130, 180, 0.1);
  transform: translateY(24%);
  margin: 0px 10px 10px 30px;
  padding: 10px ;
  width: 991px;
}
.hptext {
  color: rgba(70, 130, 180, 0.9);
}

.wrtext {
  color: rgba(255, 38, 38, 0.9);
}

.card1 {
  color: #666;
  @extend %shadow;

  .table {
    padding: 21px;
    p {
      height: 52px;
      line-height: 52px;
      border: 1px solid #cccccc;
      overflow: hidden;
      border-#{$top}: none;
      @include flex(null, start);
      &:first-child {
        border-#{$top}: 1px solid #cccccc;
      }
      span {
      }
      .tit {
        width: 180px;
        min-width: 180px;
        height: 100%;
        text-align: center;
        border-#{$right}: 1px solid #cccccc;
        margin-#{$right}: 18px;
      }
      span.gitbox {
        flex: 1;
        height: 100%;
        overflow: hidden;
        @include flex(row, start);
        a {
          &:first-child {
            margin-#{$right}: 30px;
          }
        }
      }
    }
  }
}
#lineEcharts {
  margin-#{$top}: 30px;
  padding-#{$top}: 30px;
  @extend %shadow;
}
#maintable {
  margin-#{$top}: 30px;
  padding-#{$top}: 10px;
  @extend %shadow;
}

.chartArea {
  margin-bottom: 15px;
}
.filePlc {
  display: flex;
  flex: 1;
}
.timeMid {
  width: 20px;
  left: 0;
  right: 0;
  top: 0;
  bottom: 0;
  margin: auto;
  padding-left: 10px;
}
.Context:after {
  content: "*";
  color: red;
  position: absolute;
  top: 50px;
  left: 6px;
}
label.xrequired:after {
  content: "*";
  color: red;
  font-size: 25px;
  position: relative;
  top: 8px;
  margin-left: 3px;
}
</style>

