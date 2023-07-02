<script setup>
import { ref } from "vue";
import { computed } from "vue";
import { storeToRefs } from "pinia";
import { useRouter } from "vue-router";
import useCityStore from "@/stores/modules/city";
import cityGroup from "../city/cpns/city-group.vue";
const cityValue = ref("")
const tabActive = ref()
const router = useRouter()
const cancelClick = () => {
    router.back()
}

// 网络请求在组件中，尽量再抽取一次
// const allCity = ref()
// getCityAll().then(res => {
//     console.log(res.data)
//     allCity.value = res.data
// })

// 使用city的状态管理store
const cityStore = useCityStore()
// 调用actions中的函数
cityStore.fetchAllCitys()
// 防止解构后失去响应式
const { allCities } = storeToRefs(cityStore)
const curGroup = computed(() => allCities.value[tabActive.value])

</script>


<template>
    <div class="city-topPage">
        <van-search v-model="cityValue" shape="round" show-action placeholder="城市/区域/地点" @cancel="cancelClick" />
    </div>
</template>

<style lang="less" scoped>
.city-topPage {
    margin-top: 6px;
}
</style>

