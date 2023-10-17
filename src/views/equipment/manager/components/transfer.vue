<template>
  <div>
    <el-dialog title="设备转科" :visible.sync="open" width="50%" append-to-body :close-on-click-modal="false">

      <div class="transfer-content">
        <div class="left_content">
          <h1>目标科室</h1>
        </div>
        <div class="right_content">
          <h1>已选设备</h1>
          <el-table :data="transferArr" height="600">
            <el-table-column label="设备名称" align="center" prop="equipmentName" />
            <el-table-column label="维修编码" align="center" prop="eqCode" />
            <el-table-column label="所属科室" align="center" prop="officeName" />
            <el-table-column label="所属科室" align="center" prop="eqType" />
            <el-table-column label="操作" align="center" class-name="small-padding fixed-width">
                <el-button
                  size="mini"
                  type="text"
                  icon="el-icon-delete">
                  取消</el-button>
            </el-table-column>
          </el-table>
        </div>
      </div>

    </el-dialog>
  </div>
</template>
<script>
export default {
  data() {
    return {
      open: false,
      transferArr:[],
    }
  }
}
</script>
<style scoped lang="scss">
.transfer-content {
  width: 100%;
  height: 100%;
  border: 1px #2c3e50 solid;
  display: flex;
  flex-direction: row;
}

.left_content {
  flex: 3;
  border-right: 1px solid #2c3e50;
}

.right_content {
  flex: 7;
}
</style>
