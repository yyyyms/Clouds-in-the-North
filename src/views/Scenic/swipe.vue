<template>
  <div class="scenicSpotBody">
    <div class="title">热门景点</div>
    <div class="swipe">
      <van-swipe class="my-swipe" :autoplay="3000" indicator-color="white">
        <van-swipe-item v-for="item in swipeImg" :key="item.key">
          <img class="swipe-img" :src="item.img" alt="" />
          <div class="swipe-title">{{ item.name }}</div>
        </van-swipe-item>
      </van-swipe>
    </div>
    <div style="margin-top: 3px">
      <van-sticky>
        <van-search v-model="searchData" placeholder="请输入景点" input-align="center" />
      </van-sticky>
    </div>
    <!-- @load="onLoad" -->
    <div style="margin-top: 3%">
      <van-list v-model:loading="loading" :finished="finished" finished-text="没有更多了">
        <van-cell v-for="item in scenicSpotList" :key="item.key">
          <template #default>
            <div class="listDisplayBody" @click="goToDetails(item.key - 1)">
              <img class="listDisplayPicture" :src="item.img" alt="" />
              <div class="listDisplayBody-right">
                <h2>
                  <input type="text" :value="item.name" disabled="disabled" class="listDisplayInput" />
                </h2>
                <van-rate v-model="item.grade" :size="20" :readonly="true" color="#ffd21e" void-icon="star"
                  void-color="#eee" style="margin-top: 5px" allow-half />
                <span style="margin-left: 5px">{{ item.grade }}分 </span>
                <span style="margin-left: 8%">
                  {{ item.goTo }}人来过
                </span>
                <div style="margin-top: 5px">
                  <span>距离你约{{}}公里</span>
                  <span style="margin-left: 20px">{{ item.name }}</span>
                </div>
                <div style="margin-top: 5px">
                  <span
                    style="display:inline-block;background-color: rgb(182, 217, 236);; width: 60px; text-align: center; border-radius: 5px;">可订{{
                      item.order }}</span>
                  <span style="margin-left:20vw">项目</span>
                  <span style="color: red">￥</span>
                  <span style="font-size: 20px; color: red">{{
                    item.price
                  }}</span>
                </div>
              </div>
            </div>
          </template>
        </van-cell>
      </van-list>
    </div>
  </div>
</template>

<script setup>
import useCityStore from "@/stores/modules/city";
import { onMounted, ref } from "vue";
import router from "../../router";
//   const location = navigator.geolocation.getCurrentPosition(position => {
//   console.log('当前地理位置', position)
// })
let detail = useCityStore();
const scenicSpotList = ref([
  {
    key: 1,
    value: 1,
    name: "北京",
    grade: 4.1,
    goTo: 1231,
    order: "今日",
    price: 1000,
    message: "感受大自然气息",
    img: "https://gimg2.baidu.com/image_search/src=http%3A%2F%2Fsafe-img.xhscdn.com%2Fbw1%2Fc20edd3f-b6e3-4c81-aae7-3391d5ad4f62%3FimageView2%2F2%2Fw%2F1080%2Fformat%2Fjpg&refer=http%3A%2F%2Fsafe-img.xhscdn.com&app=2002&size=f9999,10000&q=a80&n=0&g=0n&fmt=auto?sec=1690354852&t=1fe6ca02f44e40038cbcf5d860bc350b",
  },
  {
    key: 2,
    value: 2,
    name: "上海",
    grade: 4.1,
    goTo: 1231,
    order: "今日",
    price: 1000,
    message: "感受大自然气息",
    img: "https://img2.baidu.com/it/u=3908451766,1015439416&fm=253&fmt=auto&app=120&f=JPEG?w=1380&h=800",
  },
  {
    key: 3,
    value: 3,
    name: "杭州",
    grade: 4.1,
    goTo: 1231,
    order: "今日",
    price: 1000,
    message: "感受大自然气息",
    img: "https://img2.baidu.com/it/u=4139628351,2561052656&fm=253&fmt=auto&app=138&f=JPEG?w=888&h=500",
  },
  {
    key: 4,
    value: 4,
    name: "成都",
    grade: 4.1,
    goTo: 1231,
    price: 1000,
    order: "今日",
    message: "感受大自然气息",
    img: "https://img2.baidu.com/it/u=1152155473,3878496115&fm=253&fmt=auto&app=138&f=JPEG?w=667&h=500",
  },
  {
    key: 5,
    value: 5,
    name: "珠海",
    grade: 4.1,
    goTo: 1231,
    price: 1000,
    order: "今日",
    message: "感受大自然气息",
    img: "https://img0.baidu.com/it/u=4199610329,398424804&fm=253&fmt=auto&app=138&f=JPEG?w=667&h=500",
  },
  {
    key: 6,
    value: 6,
    name: "天津",
    grade: 4.1,
    goTo: 1231,
    price: 1000,
    order: "明日",
    message: "感受大自然气息",
    img: "https://img2.baidu.com/it/u=3179578422,94024343&fm=253&fmt=auto&app=120&f=JPEG?w=1025&h=665",
  },
  {
    key: 7,
    value: 7,
    name: "大理",
    grade: 4.1,
    goTo: 1231,
    price: 1000,
    order: "明日",
    message: "感受大自然气息",
    img: "https://ns-strategy.cdn.bcebos.com/ns-strategy/upload/fc_big_pic/part-00787-203.jpg",
  },
  {
    key: 8,
    value: 8,
    name: "香港",
    grade: 4.1,
    goTo: 1231,
    price: 1000,
    order: "明日",
    message: "感受大自然气息",
    img: "https://img1.baidu.com/it/u=3072573665,4182209253&fm=253&fmt=auto&app=120&f=JPEG?w=627&h=418",
  },
  {
    key: 9,
    value: 9,
    name: "武汉",
    grade: 4.1,
    goTo: 1231,
    price: 1000,
    order: "明日",
    message: "感受大自然气息",
    img: "https://img2.baidu.com/it/u=3845866084,3170653959&fm=253&fmt=auto&app=138&f=JPEG?w=890&h=500",
  },
  {
    key: 10,
    value: 10,
    name: "厦门",
    grade: 4.1,
    goTo: 1231,
    price: 1000,
    order: "明日",
    message: "感受大自然气息",
    img: "https://img1.baidu.com/it/u=2132697520,3548432632&fm=253&fmt=auto&app=138&f=JPEG?w=500&h=500",
  },
]);
const loading = ref(false);
const finished = ref(false);
const searchData = ref("");
// const onLoad = () => {
//   // 异步更新数据
//   // setTimeout 仅做示例，真实场景中一般为 ajax 请求
//   setTimeout(() => {
//     for (let i = 0; i < 10; i++) {
//       list.value.push(list.value.length + 1);
//     }
//     // 加载状态结束
//     loading.value = false;

//     // 数据全部加载完成
//     if (list.value.length >= 40) {
//       finished.value = true;
//     }
//   }, 1000);
// };
const goToDetails = (index) => {
  router.replace("/detailPage");
  detail.scenicSpot = scenicSpotList.value;
  detail.scenicSpotShu = index;
};
const swipeImg = ref([
  {
    key: 1,
    value: 1,
    name: "北京",
    img: "https://gimg2.baidu.com/image_search/src=http%3A%2F%2Fsafe-img.xhscdn.com%2Fbw1%2Fc20edd3f-b6e3-4c81-aae7-3391d5ad4f62%3FimageView2%2F2%2Fw%2F1080%2Fformat%2Fjpg&refer=http%3A%2F%2Fsafe-img.xhscdn.com&app=2002&size=f9999,10000&q=a80&n=0&g=0n&fmt=auto?sec=1690354852&t=1fe6ca02f44e40038cbcf5d860bc350b",
  },
  {
    key: 2,
    value: 2,
    name: "上海",
    img: "https://img2.baidu.com/it/u=3908451766,1015439416&fm=253&fmt=auto&app=120&f=JPEG?w=1380&h=800",
  },
  {
    key: 3,
    value: 3,
    name: "杭州",
    img: "https://img2.baidu.com/it/u=4139628351,2561052656&fm=253&fmt=auto&app=138&f=JPEG?w=888&h=500",
  },
  {
    key: 4,
    value: 4,
    name: "成都",
    img: "https://img2.baidu.com/it/u=1152155473,3878496115&fm=253&fmt=auto&app=138&f=JPEG?w=667&h=500",
  },
  {
    key: 5,
    value: 5,
    name: "珠海",
    img: "https://img0.baidu.com/it/u=4199610329,398424804&fm=253&fmt=auto&app=138&f=JPEG?w=667&h=500",
  },
  {
    key: 6,
    value: 6,
    name: "天津",
    img: "https://img2.baidu.com/it/u=3179578422,94024343&fm=253&fmt=auto&app=120&f=JPEG?w=1025&h=665",
  },
  {
    key: 7,
    value: 7,
    name: "大理",
    img: "https://ns-strategy.cdn.bcebos.com/ns-strategy/upload/fc_big_pic/part-00787-203.jpg",
  },
  {
    key: 8,
    value: 8,
    name: "香港",
    img: "https://img1.baidu.com/it/u=3072573665,4182209253&fm=253&fmt=auto&app=120&f=JPEG?w=627&h=418",
  },
  {
    key: 9,
    value: 9,
    name: "武汉",
    img: "https://img2.baidu.com/it/u=3845866084,3170653959&fm=253&fmt=auto&app=138&f=JPEG?w=890&h=500",
  },
  {
    key: 10,
    value: 10,
    name: "厦门",
    img: "https://img1.baidu.com/it/u=2132697520,3548432632&fm=253&fmt=auto&app=138&f=JPEG?w=500&h=500",
  },
]);
onMounted(() => { });
</script>

<style lang="less" scoped>
.scenicSpotBody {
  background-color: #f4f5f7;
}

.title {
  font-size: 18px;
  font-weight: 800;
  padding-top: 12px;
  color: var(--primary-color);
  text-align: center;
}

.swipe {
  margin-top: 14px;

  &.my-swipe .van-swipe-item {
    color: #fff;
    font-size: 20px;
    line-height: 150px;
    text-align: center;
    background-color: #39a9ed;
  }

  &-title {
    width: 45px;
    border-radius: 20px;
    font-size: 14px;
    position: absolute;
    background-color: #fff;
    bottom: 5px;
    right: 5px;
    color: black;
    text-align: center;
    // background-color: var(--primary-color);
  }

  &-img {
    border-radius: 6px;
    height: 28vh;
    width: 100%;
  }
}

.listDisplayBody {
  width: 97%;
  height: 82%;
  padding: 5px;
  background-color: white;
  border: 1px white solid;
  border-radius: 10px;
  display: flex;
}

.listDisplayPicture {
  width: 100px;
  height: 120px;
  padding: 10px;
}

.van-cell {
  background-color: #f4f5f7;
  padding: 0px;
  height: 170px;
  width: 95%;
  margin: 0 auto;
}

.listDisplayInput {
  border-style: none;
  background-color: white;
}

.listDisplayBody-right {
  padding: 14px;
  width: 100%;
}
</style>
