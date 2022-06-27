<template>
  <div>
    <my-table :goodsList="goodsList">
      <template #biaotou>
        <th>#</th>
        <th>商品名称</th>
        <th>价格</th>
        <th>标签</th>
        <th>操作</th>
      </template>
      <template #neirong="{ item }">
        <td>{{ item.id }}</td>
        <td>{{ item.goods_name }}</td>
        <td>{{ item.goods_price }}</td>
        <td>
          <add-tag @add-tag="addTag(item.tags, $event)"></add-tag>
          <span
            class="badge bg-warning text-dark"
            v-for="(i, index) in item.tags"
            :key="index"
            style="margin-right: 5px"
            >{{ i }}</span
          >
        </td>
        <td>
          <button class="btn btn-danger btn-sm" @click="delGoods(item.id)">
            删除
          </button>
        </td>
      </template>
    </my-table>
  </div>
</template>

<script>
import MyTable from '@/components/MyTable.vue'
import axios from '@/utils/request.js'
import AddTag from '../components/AddTag.vue'
export default {
  components: {
    MyTable,
    AddTag
  },
  created() {
    this.getGoodsList()
  },
  data() {
    return {
      goodsList: []
    }
  },
  methods: {
    async getGoodsList() {
      const { data } = await axios({ url: '/api/goods' })
      this.goodsList = data.data
    },
    delGoods(id) {
      this.goodsList = this.goodsList.filter((item) => item.id !== id)
    },
    addTag(tags, tagName) {
      tags.push(tagName)
    }
  }
}
</script>

<style></style>
