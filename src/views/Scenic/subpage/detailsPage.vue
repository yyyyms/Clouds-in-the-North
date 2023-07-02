<template>
  <div class="main-body">
    <div style="position: sticky; top: 0; z-index: 100">
      <van-nav-bar
        :title="detailData[detailNum].name"
        left-text="返回"
        left-arrow
        @click-left="goToAll"
      />
    </div>
    <div style="position: sticky; top: 7%; z-index: 1">
      <!-- <van-sticky z-index="-1"> -->
      <img
        :src="detailData[detailNum].img"
        alt=""
        style="width: 100%; height: 280px; border-radius: 10px"
      />
      <!-- </van-sticky> -->
    </div>
    <div style="position: relative; margin-top: 5px; z-index: 99">
      <div class="detail-main-body">
        <h2>{{ detailData[detailNum].name }}</h2>
        <div class="detail-main-body-rate">
          <h2>{{ detailData[detailNum].grade }}分</h2>
        </div>
      </div>
      <div class="detail-main-body-message">
        <span>"{{ detailData[detailNum].message }}"</span>
      </div>
      <div class="detail-main-distance">
        <h3 style="padding-bottom: 10px">距离你约1000公里</h3>
      </div>
      <div
        style="
          position: relative;
          width: 100%;
          height: 10px;
          background-color: #f4f5f7;
        "
      ></div>
      <div class="detail-mian-sale">
        <div style="display: flex">
          <van-button
            plain
            type="default"
            color="gray"
            @click="buttonData = 1"
            class="detail-main-sale-button"
            :class='buttonData==1?"detail-main-sale-button-button":""'
            >可订{{ detailData[detailNum].order }}</van-button
          >
          <van-button
            plain
            type="default"
            color="gray"
            @click="buttonData = 2"
            class="detail-main-sale-button"
            :class='buttonData==2?"detail-main-sale-button-button":""'
            >可订{{ detailData[detailNum].order }}</van-button
          >
          <van-button
            plain
            type="default"
            color="gray"
            @click="buttonData = 3"
            class="detail-main-sale-button"
            :class='buttonData==3?"detail-main-sale-button-button":""'
            >可订{{ detailData[detailNum].order }}</van-button
          >
        </div>
        <h2 style="margin-top: 3%">通票</h2>
        <div class="detail-mian-sale-sale">
          <h2>成人票</h2>
          <div>
            <h2 style="color: red; margin-top: 1%">
              ￥{{ detailData[detailNum].price }}
            </h2>
          </div>
          <div class="detail-mian-sale-sale-order">
            <h6>可订{{ detailData[detailNum].order }}</h6>
          </div>
          <div
            style="
              margin-top: -17%;
              margin-left: 85%;
              padding-bottom: 10px;
              font-size: 22px;
            "
          >
            <van-button type="warning" style="border-radius: 100px; width: 70px"
              >订购</van-button
            >
          </div>
          <hr />
          <h2>成人票</h2>
          <div>
            <h2 style="color: red; margin-top: 1%">
              ￥{{ detailData[detailNum].price }}
            </h2>
          </div>
          <div class="detail-mian-sale-sale-order">
            <h6>可订{{ detailData[detailNum].order }}</h6>
          </div>
          <div
            style="
              margin-top: -17%;
              margin-left: 85%;
              padding-bottom: 10px;
              font-size: 22px;
            "
          >
            <van-button type="warning" style="border-radius: 100px; width: 70px"
              >订购</van-button
            >
          </div>
          <hr />
          <h2>成人票(夜场)</h2>
          <div>
            <h2 style="color: red; margin-top: 1%">
              ￥{{ detailData[detailNum].price }}
            </h2>
          </div>
          <div class="detail-mian-sale-sale-order">
            <h6>可订{{ detailData[detailNum].order }}</h6>
          </div>
          <div
            style="
              margin-top: -17%;
              margin-left: 85%;
              padding-bottom: 10px;
              font-size: 22px;
            "
          >
            <van-button type="warning" style="border-radius: 100px; width: 70px"
              >订购
            </van-button>
          </div>
        </div>
        <div>
          <homecontent />
        </div>
      </div>
    </div>
  </div>
</template>
<script setup>
import useCityStore from "@/stores/modules/city";
import router from "../../../router";
import homecontent from "../../home/cpns/home-content.vue";
import { ref } from "vue";
const goToAll = () => {
  router.back();
};
const buttonData = ref(1)
let detail = useCityStore();
let detailData = detail.scenicSpot;
let detailNum = detail.scenicSpotShu;
</script>
<style lang="less" scoped>
.main-body {
  background-color: #f4f5f7;
  position: relative;
}
.detail-main-body {
  padding: 20px;
  display: flex;
  background-color: #fff;
}
.detail-main-body-rate {
  background-color: rgb(200, 234, 243);
  border-radius: 5px;
  border: rgb(180, 225, 237) 1px solid;
  margin-left: 73%;
  color: rgb(78, 91, 226);
  padding: 3px;
}
.detail-main-distance {
  padding-left: 20px;
  padding-right: 20px;
  background-color: #fff;
}
.detail-mian-sale {
  padding: 20px;
  background-color: #fff;
  // margin-top: 10px;
}
.detail-main-sale-button {
  border: none;
  border-radius: 5px;
  background-color: #f4f5f7;
  margin-left: 2%;
  &.detail-main-sale-button-button{
    background-color: #ECF5FF;
    color: #4FA6FF;
  }
}
.detail-mian-sale-sale {
  margin-top: 20px;
  padding: 20px;
  background-color: #f4f5f7;
  border-radius: 5px;
  border: #f4f5f7 1px solid;
}
.detail-mian-sale-sale-order {
  width: 16%;
  margin-top: -3%;
  background-color: rgb(200, 234, 243);
  color: blue;
  text-align: center;
}
.detail-main-body-message {
  padding-left: 20px;
  padding-right: 20px;
  background-color: #fff;
  margin-top: -20px;
  padding-bottom: 15px;
}
</style>
