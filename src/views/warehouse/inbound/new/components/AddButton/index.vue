<template>
  <el-button v-permission="permission" type="success" size="mini" icon="el-icon-plus" @click="handler">
    新增
  </el-button>
</template>
<script>
import permission from '@/directive/permission/index.js' // 权限判断指令
export default {
  directives: { permission },
  props: {
    permission: {
      type: Array,
      default: () => ([])
    }
  },
  methods: {
    handler() {
      this.$router.push({ path: '/warehouse/inbound/new/components/addform' })
    }
  }
}
</script>
