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
        title: '物料信息',
        url: '/api/v1/material',
        columns: [
          {
            name: 'code',
            type: 'input',
            label: '物料编码',
            formConfig: {
              rules: [{ required: true, message: '物料编码不能为空' }],
              edit: { disabled: true }
            }
          },
          {
            name: 'name',
            formConfig: {
              rules: [{ required: true, message: '物料名称不能为空' }]
            },
            label: '物料名称'
          },
          {
            name: 'spec',
            type: 'input',
            label: '规格'
          },
          {
            name: 'brand',
            type: 'input',
            label: '品牌'
          },
          {
            name: 'model',
            type: 'input',
            label: '型号'
          },
          {
            name: 'unit',
            type: 'input',
            label: '单位'
          },
          {
            name: 'supplier',
            type: 'input',
            label: '供应商'
          },
          {
            name: 'status',
            type: 'select',
            label: '状态'
          },
          {
            name: 'remark',
            label: '备注',
            formConfig: {
              type: 'textarea'
            },
            searchConfig: {
              hidden: true
            }
          }
        ]
      }
    }
  }
}
</script>
