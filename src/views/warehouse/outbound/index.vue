<template>
  <el-tabs v-model="activeName" type="card">
    <el-tab-pane label="未完成单据" name="first"><cdp-table :table-config="tableConfig" /></el-tab-pane>
    <el-tab-pane label="已完成单据" name="second"><cdp-table :table-config="tableConfig" /></el-tab-pane>
    <el-tab-pane label="未审核单据" name="third"><cdp-table :table-config="tableConfig" /></el-tab-pane>
    <el-tab-pane label="已审核单据" name="fourth"><cdp-table :table-config="tableConfig" /></el-tab-pane>
  </el-tabs>
</template>
<script>
import CdpTable from '@/components/cdp-ui/cdp-template/cdp-table'

export default {
  components: {
    CdpTable
  },
  data() {
    return {
      activeName: 'first',
      tableConfig: {
        title: '出库管理',
        columns: [
          { name: 'code', label: '单据号' },
          { name: 'source', label: '单据来源' },
          { name: 'date', label: '单据日期' },
          { name: 'warehouse', label: '仓库' },
          { name: 'type', label: '出入库类型' },
          { name: 'status', label: '单据状态' },
          { name: 'user', label: '业务员' },
          { name: 'dept', label: '业务部门' }
        ]
      }
    }
  }
}
</script>
