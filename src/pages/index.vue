<!--
 * @FileDescription: 登陆
 * @Author: jack
 * @Date: 2023-1-2
 * @LastEditors: jack
 * @LastEditTime: 2023-1-2
 -->
<script lang="ts" setup>
import { reactive } from 'vue'

const form = reactive({ username: 'admin', password: '123456', mode: '01' })

const loginHandle = async () => {
  const { data } = await useFetch('/api/login', { method: 'POST', body: form })
  console.log('data=',data)
}
</script>

<template>
  <div class="pt-16">

    <div class="p-5">
      <div class="">登陆</div>{{ form }}

      <div class="pt-1 pb-1">
        <div class="pb-1 font-medium">用户名</div>
        <div
          class="max-w-md mb-1 overflow-hidden border border-gray-400 rounded-lg formkit-invalid:border-red-500 focus-within:border-blue-500">
          <input
            class="w-full h-10 px-3 text-base text-gray-700 placeholder-gray-400 bg-white border-none rounded-lg focus:outline-none"
            v-model="form.username" placeholder="请输入用户名" />
        </div>
      </div>

      <div class="pt-1 pb-1">
        <div class="pb-1 font-medium">密码</div>
        <div
          class="max-w-md mb-1 overflow-hidden border border-gray-400 rounded-lg formkit-invalid:border-red-500 focus-within:border-blue-500">
          <input
            class="w-full h-10 px-3 text-base text-gray-700 placeholder-gray-400 bg-white border-none rounded-lg focus:outline-none"
            v-model="form.password" placeholder="请输入密码" />
        </div>
      </div>

      <div>
        <button @click="loginHandle">登陆</button>
      </div>

    </div>
  </div>
</template>

<style scoped>
button {
  background-color: #4CAF50;
  border: none;
  color: white;
  padding: 15px 32px;
  text-align: center;
  text-decoration: none;
  display: inline-block;
  font-size: 16px;
}
</style>