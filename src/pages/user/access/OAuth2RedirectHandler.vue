<script setup>
import { useRoute, useRouter } from 'vue-router'
import { useUserStore } from '@/stores/userStore'

const route = useRoute()
const router = useRouter()
const userStore = useUserStore()

// sns 로그인 처리
const accessToken = route.query.accessToken
if (accessToken) {
  localStorage.setItem("accessToken", accessToken);

  //회원 정보 저장
  userStore.setLoginInfo({
    id: route.query.id,
    role: route.query.role
  }, accessToken);

  router.push('/')
} else {
  alert("로그인 실패")
  router.push('/login/fail')
}
</script>

<template>
  <p>로그인 처리 중...</p>
</template>
