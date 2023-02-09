<template>
  <el-table :data="tableData">
    <el-table-column label="物料编码" prop="code" />
  </el-table>
</template>

<script>

export default {
  data() {
    return {
      tableData: [
        { code: '100001' }
      ]
    }
  }
}
</script>
