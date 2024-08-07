<script setup>
import { ref } from 'vue'

const items = ref([
  { id: 1, name: '珍珠奶茶', description: '香濃奶茶搭配QQ珍珠', price: 50, stock: 20, editing: false },
  { id: 2, name: '冬瓜檸檬', description: '清新冬瓜配上新鮮檸檬', price: 45, stock: 18, editing: false },
  { id: 3, name: '翡翠檸檬', description: '綠茶與檸檬的完美結合', price: 55, stock: 34, editing: false },
  { id: 4, name: '四季春茶', description: '香醇四季春茶，回甘無比', price: 45, stock: 10, editing: false },
  { id: 5, name: '阿薩姆奶茶', description: '阿薩姆紅茶搭配香醇鮮奶', price: 50, stock: 25, editing: false },
  { id: 6, name: '檸檬冰茶', description: '檸檬與冰茶的清新組合', price: 45, stock: 20, editing: false },
  { id: 7, name: '芒果綠茶', description: '芒果與綠茶的獨特風味', price: 55, stock: 18, editing: false },
  { id: 8, name: '抹茶拿鐵', description: '抹茶與鮮奶的絕配', price: 60, stock: 20, editing: false },
])

const decreaseStock = (item) => {
  if (item.stock > 0) item.stock--
}

const increaseStock = (item) => {
  item.stock++
}

const toggleEdit = (item) => {
  item.editing = !item.editing
}
</script>

<template>
  <div>
    <h1>餐點管理工具</h1>
    <table>
      <thead>
        <tr>
          <th>品項</th>
          <th>描述</th>
          <th>價格</th>
          <th>庫存</th>
        </tr>
      </thead>
      <tbody>
        <tr v-for="item in items" :key="item.id">
          <td>
            <span v-if="!item.editing">{{ item.name }}</span>
            <input v-else v-model="item.name" @keyup.enter="toggleEdit(item)" />
            <button @click="toggleEdit(item)">
              {{ item.editing ? '儲存' : '編輯' }}
            </button>
          </td>
          <td>{{ item.description }}</td>
          <td>{{ item.price }}</td>
          <td>
            <button @click="decreaseStock(item)">-</button>
            {{ item.stock }}
            <button @click="increaseStock(item)">+</button>
          </td>
        </tr>
      </tbody>
    </table>
  </div>
</template>

<style>
body {
  background-color: white !important;
  color: black !important;
}

table {
  width: 100%;
  border-collapse: collapse;
}

th, td {
  border: 1px solid #ddd;
  padding: 8px;
}

th {
  background-color: #f2f2f2;
}

button {
  margin: 0 5px;
}
</style>
