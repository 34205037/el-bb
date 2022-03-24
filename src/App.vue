<script setup lang="ts">
import { reactive } from 'vue';

const data = reactive({
  email_1: "",
  email_2: ""
});

const rules = reactive({
  email_1: [
    {
      required: true,
      message: 'Please input email address',
      trigger: 'blur',
    },
    {
      type: 'email',
      message: 'Please input correct email address',
      trigger: ['blur', 'change'],
    },
  ],
})
</script>

<template>
  <!-- 给form设置rules，只要验证规则里包含type，给type指定任何值，都提示与类型签名不兼容 -->
  <el-form ref="form" :model="data" :rules="rules">

    <el-form-item label="email" prop="email_1">
      <el-input v-model="data.email_1" autocomplete="off-x" />
    </el-form-item>

    <!-- 直接给form-item设置rules，正确显示类型声明，没有错误提示 -->
    <el-form-item
      label="email"
      prop="email_2"
      :rules="[
        {
          required: true,
          message: 'Please input email address',
          trigger: 'blur',
        },
        {
          type: 'email',
          message: 'Please input correct email address',
          trigger: ['blur', 'change'],
        },
      ]"
    >
      <el-input v-model="data.email_2" autocomplete="off-x" />
    </el-form-item>
  </el-form>
</template>
