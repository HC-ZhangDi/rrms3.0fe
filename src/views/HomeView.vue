<script setup lang="ts">
import { ref } from 'vue'

interface ReservationData {
  id: number
  customerName: string
  phone: string
  service: string
  datetime: string
  status: string
}

const tableData = ref<ReservationData[]>([
  {
    id: 1,
    customerName: '张三',
    phone: '138****1234',
    service: '常规体检',
    datetime: '2024-01-15 09:00',
    status: '已确认'
  },
  {
    id: 2,
    customerName: '李四',
    phone: '139****5678',
    service: '专科检查',
    datetime: '2024-01-16 14:30',
    status: '待确认'
  },
  {
    id: 3,
    customerName: '王五',
    phone: '137****9012',
    service: '全身体检',
    datetime: '2024-01-17 10:15',
    status: '已完成'
  }
])
</script>

<template>
  <div class="home-container">
    <h2>预约管理</h2>
    <div class="table-container">
      <table>
        <thead>
          <tr>
            <th>预约号</th>
            <th>客户姓名</th>
            <th>联系电话</th>
            <th>预约项目</th>
            <th>预约时间</th>
            <th>状态</th>
          </tr>
        </thead>
        <tbody>
          <tr v-for="item in tableData" :key="item.id">
            <td>{{ item.id }}</td>
            <td>{{ item.customerName }}</td>
            <td>{{ item.phone }}</td>
            <td>{{ item.service }}</td>
            <td>{{ item.datetime }}</td>
            <td>
              <span :class="['status', item.status]">{{ item.status }}</span>
            </td>
          </tr>
        </tbody>
      </table>
    </div>
  </div>
</template>

<style scoped>
.home-container {
  padding: 2rem;
}

.table-container {
  margin-top: 1rem;
  overflow-x: auto;
}

table {
  width: 100%;
  border-collapse: collapse;
  background-color: white;
  box-shadow: 0 1px 3px rgba(0, 0, 0, 0.1);
}

th, td {
  padding: 0.75rem;
  text-align: left;
  border-bottom: 1px solid #eee;
}

th {
  background-color: #f8f9fa;
  font-weight: 600;
}

tr:hover {
  background-color: #f8f9fa;
}
.status {
  padding: 4px 8px;
  border-radius: 4px;
  font-size: 0.875rem;
}

.status.已确认 {
  background-color: #e6f4ff;
  color: #1677ff;
}

.status.待确认 {
  background-color: #fff7e6;
  color: #faad14;
}

.status.已完成 {
  background-color: #f6ffed;
  color: #52c41a;
}
</style>