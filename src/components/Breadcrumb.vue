<script setup lang="ts">
import { ref, watch } from 'vue'
import { useRoute, RouterLink } from 'vue-router'

interface BreadcrumbItem {
  name: string
  path: string
}

const route = useRoute()
const breadcrumbItems = ref<BreadcrumbItem[]>([])

// 获取面包屑显示名称
function getBreadcrumbName(path: string): string {
  const nameMap: Record<string, string> = {
    'home': '首页',
    'about': '关于我们'
    // 可以根据需要添加更多路由映射
  }
  return nameMap[path] || path
}

// 监听路由变化更新面包屑
watch(
  () => route.path,
  () => {
    const paths = route.path.split('/').filter(item => item)
    breadcrumbItems.value = [
      { name: '首页', path: '/' },
      ...paths.map((path, index) => {
        const fullPath = '/' + paths.slice(0, index + 1).join('/')
        return {
          name: getBreadcrumbName(path),
          path: fullPath
        }
      })
    ]
  },
  { immediate: true }
)
</script>

<template>
  <nav class="breadcrumb">
    <ol>
      <li v-for="(item, index) in breadcrumbItems" :key="index">
        <RouterLink v-if="index < breadcrumbItems.length - 1" :to="item.path">
          {{ item.name }}
        </RouterLink>
        <span v-else>{{ item.name }}</span>
        <span v-if="index < breadcrumbItems.length - 1" class="separator">/</span>
      </li>
    </ol>
  </nav>
</template>

<style scoped>
.breadcrumb {
  padding: 0.5rem 2rem;
  background-color: #fff;
}

.breadcrumb ol {
  list-style: none;
  margin: 0;
  padding: 0;
  display: flex;
  align-items: center;
}

.breadcrumb li {
  display: flex;
  align-items: center;
}

.breadcrumb a {
  color: #666;
  text-decoration: none;
}

.breadcrumb a:hover {
  color: #333;
  text-decoration: underline;
}

.breadcrumb .separator {
  margin: 0 0.5rem;
  color: #999;
}
</style>