<template>
  <cdp-table :table-config="tableConfig" />
</template>

<script>
import CdpTable from '@/components/cdp-ui/cdp-template/cdp-table'

export default {
  components: {
    CdpTable
  },
  data() {
    return {
      tableConfig: {
        title: '入库管理',
        columns: [
          { name: 'code', label: '单据号' },
          { name: 'source', label: '单据来源' },
          { name: 'in', label: '进货方' },
          { name: 'out', label: '供货方' },
          { name: 'date', label: '单据日期' },
          { name: 'warehouse', label: '仓库' },
          { name: 'type', label: '出入库类型' },
          { name: 'status', label: '单据状态' },
          { name: 'user', label: '业务员' }
        ]
      }
    }
  }
}
</script>
