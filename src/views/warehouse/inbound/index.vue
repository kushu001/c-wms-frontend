<template>
  <el-tabs v-model="activeName" type="card">
    <el-tab-pane label="未完成单据" name="first"><New /></el-tab-pane>
    <el-tab-pane label="审核中的单据" name="second"><Processing /></el-tab-pane>
    <el-tab-pane label="全部" name="third"><All /></el-tab-pane>
  </el-tabs>
</template>
<script>
import New from './new'
import Processing from './processing'
import All from './all'

export default {
  components: {
    New,
    Processing,
    All
  },
  data() {
    return {
      activeName: 'first'
    }
  }
}
</script>
