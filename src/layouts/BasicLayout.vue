<script setup lang="ts">
import {ref} from "vue";
import {Toast} from "vant";
import Team from "../pages/Team.vue";
import Index from "../pages/Index.vue";

const onClickLeft = () => alert("left");
const onClickRight = () => alert("right");
const active = ref("index");
const onChange = (index: string) => Toast.success(`标签 ${index}`);
</script>

<template>
  <van-nav-bar title="标题" left-arrow
               @click-left="onClickLeft"
               @click-right="onClickRight">
    <template #right>
      <van-icon name="search" size="18" />
    </template>

  </van-nav-bar>
  <div id="content">
    <template v-if="active === 'index'">
      <Index />
    </template>
    <template v-if="active === 'team'">
      <Team />
    </template>

  </div>

  <van-tabbar v-model="active" @change="onChange">
    <van-tabbar-item icon="home" name="index">主页</van-tabbar-item>
    <van-tabbar-item icon="search" name="team">队伍</van-tabbar-item>
    <van-tabbar-item icon="friends" name="user">个人</van-tabbar-item>
  </van-tabbar>
</template>

<style scoped>

</style>