<script setup lang="ts">
import { useMemberStore } from '@/stores'
import { http } from '@/utils/http'

const memberStore = useMemberStore()
// 测试请求
const getData = async () => {
  const res = await http({
    method: 'GET',
    url: '/home/banner',
    header: {},
  })
  console.log('logger = >', res)
}
</script>

<template>
  <view class="my">
    <view>会员信息：{{ memberStore.profile }} </view>
    <button
      @tap="
        memberStore.setProfile({
          nickname: 'bwz',
          token: '123',
        })
      "
      size="mini"
      plain
      type="primary"
    >
      保存用户信息
    </button>
    <button @tap="memberStore.clearProfile()" size="mini" plain type="warn">清理用户信息</button>
    <button @click="getData()" size="mini" plain type="primary">测试请求</button>
  </view>
</template>

<style lang="scss">
//
</style>
