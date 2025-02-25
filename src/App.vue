<script setup lang="ts">
import { RouterLink, RouterView } from 'vue-router'
import Breadcrumb from './components/Breadcrumb.vue'
import NotificationBar from './components/NotificationBar.vue'
</script>

<template>
  <header>
    <div class="wrapper header-container">
      <h1 class="site-title">RRMS</h1>
      <nav class="main-nav">
        <RouterLink to="/">Home</RouterLink>
        <RouterLink to="/about">About</RouterLink>
      </nav>
    </div>
  </header>

  <main>
    <!-- 消息通知栏 -->
    <NotificationBar />

    <!-- 面包屑导航组件 -->
    <Breadcrumb />

    <RouterView />
  </main>

  <footer class="footer">
    <div class="copyright">
      <!-- 页脚版权信息 -->
      <p>&copy; {{ new Date().getFullYear() }} RRMS. All rights reserved.</p>
    </div>
  </footer>

</template>

<style scoped>
.app-container {
  min-height: 100vh;
  padding-bottom: 4rem;
}

.header-container {
  display: flex;
  justify-content: space-between;
  align-items: center;
  padding: 1rem 2rem;
  background-color: rgba(69, 69, 69, 0.5);
}

.site-title {
  margin: 0;
}

.main-nav {
  display: flex;
  gap: 1.5rem;
}

.footer {
  position: fixed;
  bottom: 0;
  left: 0;
  width: 100%;
  background-color: rgba(240, 240, 240, 0.5);
  /* 添加淡色背景 */
  margin-top: 0;
  padding: 1rem;
  text-align: center;
  border-top: 1px solid var(--color-border);
}

.copyright {
  font-size: 0.875rem;
  color: var(--color-text-light);
}
</style>
