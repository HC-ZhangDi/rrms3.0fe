<script setup lang="ts">
import { ref } from 'vue'

const notices = ref([
  "系统维护通知：本周六凌晨2点-4点进行系统维护，请提前做好准备",
  "新功能上线：资源预约系统已更新，支持批量预约功能",
  "温馨提示：请及时更新个人信息，确保信息准确性"
])
</script>

<template>
  <div class="notification-bar">
    <div class="notification-content">
      <div v-for="(notice, index) in notices" :key="index" class="notice-item">
        {{ notice }}
      </div>
    </div>
  </div>
</template>

<style scoped>
.notification-bar {
  width: 100%;
  height: 40px;
  background-color: #fff9e6;
  overflow: hidden;
  position: relative;
}

.notification-content {
  position: absolute;
  animation: scrollNotice 5s linear infinite;
  display: flex;
  flex-direction: column;
}

.notice-item {
  height: 40px;
  padding: 0 20px;
  line-height: 40px;
  color: #666;
}

@keyframes scrollNotice {
  0%, 25% {
    transform: translateY(0);
  }
  33%, 58% {
    transform: translateY(-40px);
  }
  66%, 91% {
    transform: translateY(-80px);
  }
  100% {
    transform: translateY(-120px);
  }
}
</style>