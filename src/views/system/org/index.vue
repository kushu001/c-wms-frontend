<template>
  <div>
    <cdp-table ref="table" :table-config="tableConfig" :operations="['add', 'import', 'export']">
      <template v-slot:tableOperations="slotProps">
        <el-button type="text" style="margin-left:10px" size="small" @click="dialogFormHandler(slotProps)">新 增</el-button>
      </template>
    </cdp-table>
    <el-dialog title="新增子公司/部门" :visible.sync="dialogVisible">
      <el-form ref="form" :inline="true" :model="form" :rules="rules" label-width="120px">
        <el-form-item label="公司/部门名称" prop="name">
          <el-input v-model="form.name" />
        </el-form-item>
        <el-form-item label="部门代码" prop="code">
          <el-input v-model="form.code" />
        </el-form-item>
        <el-form-item label="部门负责人" prop="manager_id">
          <cdp-user-select-table v-model="form.manager_id" style="width:183px" />
        </el-form-item>
      </el-form>
      <div slot="footer" class="dialog-footer">
        <el-button @click="dialogVisible = false">取 消</el-button>
        <el-button type="primary" @click="onSubmit">确 定</el-button>
      </div>
    </el-dialog>
  </div>
</template>
<script>

import CdpTable from '@/components/cdp-ui/cdp-template/cdp-table'
import CdpUserSelectTable from '@/views/components/cdp-user-select-table'
import { add } from '@/api/api'
export default {
  name: 'Org',
  components: {
    CdpTable,
    CdpUserSelectTable
  },
  data() {
    return {
      tableConfig: {
        title: '部门',
        url: '/api/v1/org',
        pagination: false,
        operations: ['add'],
        columns: [
          {
            name: 'name',
            label: '公司/部门名称',
            formConfig: {
              rules: [{ required: true, message: '请输入公司/部门名称', trigger: 'blur' }]
            }
          },
          {
            name: 'manager',
            formConfig: {
              name: 'manager_id',
              type: 'user-select-table',
              rules: [{ required: true, message: '请选择负责人' }]
            },
            label: '部门负责人'
          },
          {
            name: 'create_time',
            label: '创建日期',
            formConfig: {
              hidden: true
            },
            searchConfig: {
              hidden: true
            }
          }
        ]
      },
      form: {
        name: '',
        code: '',
        manager_id: '',
        pid: 0
      },
      rules: {
        name: [{ required: true, message: '请输入公司/部门名称', trigger: 'blur' }],
        manager_id: [{ required: true, message: '请选择负责人' }]
      },
      dialogVisible: false

    }
  },
  methods: {
    onSubmit() {
      this.$refs.form.validate((error, errrorInfo) => {
        if (!error) {
          return
        }
        add(this.form, '/api/v1/org').then(({ data }) => {
          if (data.code === 200) {
            this.$message({
              type: 'success',
              message: '新建成功'
            })
            this.$refs.form.resetFields()
            this.$refs.table.refresh()
          } else {
            this.$message({
              type: 'danger',
              message: '新建失败'
            })
          }
          this.dialogVisible = false
        })
      })
    },
    dialogFormHandler({ row }) {
      this.dialogVisible = true
      this.form.pid = row.id
    },
    sizeChangeHandler(pageSize) {
      console.log(`每页条数:${pageSize}`)
    },
    currentChangeHandler(currentPage) {
      console.log(`当前页:${currentPage}`)
    },
    preClickHandler(currentPage) {
      console.log(`上一页:${currentPage}`)
    },
    nextClickHandler(currentPage) {
      console.log(`下一页:${currentPage}`)
    }
  }
}
</script>
