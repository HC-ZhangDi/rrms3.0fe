<script setup lang="ts">
interface Product {
  id: number
  name: string
  description: string
  category: string
  price: string
}

const products = [
  {
    id: 1,
    name: '智能预约系统',
    description: '基于AI的智能预约管理解决方案',
    category: '软件服务',
    price: '联系获取'
  },
  {
    id: 2,
    name: '资源调度平台',
    description: '高效的资源分配与管理系统',
    category: '企业软件',
    price: '联系获取'
  },
  {
    id: 3,
    name: '数据分析套件',
    description: '预约数据可视化与分析工具',
    category: '数据服务',
    price: '联系获取'
  }
]
</script>

<template>
  <div class="about-container">
    <h2>产品介绍</h2>
    <div class="table-container">
      <table>
        <thead>
          <tr>
            <th>产品名称</th>
            <th>描述</th>
            <th>类别</th>
            <th>价格</th>
          </tr>
        </thead>
        <tbody>
          <tr v-for="product in products" :key="product.id">
            <td class="product-name">{{ product.name }}</td>
            <td>{{ product.description }}</td>
            <td>{{ product.category }}</td>
            <td>{{ product.price }}</td>
          </tr>
        </tbody>
      </table>
    </div>
  </div>
</template>

<style scoped>
.about-container {
  padding: 2rem;
}

.table-container {
  margin-top: 2rem;
  overflow-x: auto;
  background-color: white;
  border-radius: 8px;
  box-shadow: 0 2px 4px rgba(0, 0, 0, 0.1);
}

table {
  width: 100%;
  border-collapse: collapse;
}

th, td {
  padding: 1rem;
  text-align: left;
  border-bottom: 1px solid #eee;
}

th {
  background-color: #f8f9fa;
  font-weight: 600;
  color: #333;
}

.product-name {
  font-weight: 500;
  color: #2c3e50;
}

tr:hover {
  background-color: #f8f9fa;
}

h2 {
  color: #2c3e50;
  margin-bottom: 1rem;
}
</style>