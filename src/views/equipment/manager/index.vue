<template>
  <div class="app-container">
    <div class="box">
      <LeftClass class="left-class"></LeftClass>
      <div class="right_content">
        <el-table :data="configList" :row-key="(row) => { return row.equipmentId }">
          <template slot-scope="scope">
            <el-table-column label="设备名称" align="center" prop="equipmentName"/>
            <el-table-column label="维修编码" align="center" prop="eqCode"/>
            <el-table-column label="所属科室" align="center" prop="officeName"/>
            <el-table-column label="设备分类" align="center" prop="eqType"/>
            <el-table-column label="操作" align="center" class-name="small-padding fixed-width" width="400"
                             fixed="right">
              <el-button size="mini" type="text" icon="el-icon-edit">修改</el-button>
              <el-button size="mini" type="text" icon="el-icon-delete"  @click="handleTransfer(scope.row)">设备转科</el-button>
            </el-table-column>
          </template>


        </el-table>
      </div>
    </div>
    <!-- 设备转科 -->
    <Transfer ref="transfer" />

  </div>
</template>
<script>
import LeftClass from "@/views/equipment/manager/components/leftClass.vue";
import Transfer from "@/views/equipment/manager/components/transfer.vue";

export default {
  name: "Manager",
  components: {
    Transfer,
    LeftClass,
  },
  data() {
    return {
      // 遮罩层
      loading: true,
      // 参数配置表格数据
      configList: [],
    };
  },
  created() {
    this.getList();
  },
  methods: {
    // 设备转科
    handleTransfer(row){
      console.log('row==========', row);
      let transferList = [row];
      console.log('transferList==========', transferList);
      this.$refs.transfer.transferArr = transferList
      this.$refs.transfer.open = true
    },
    // 查询列表
    getList() {
      this.loading = true;
      this.configList = [
        {
          equipmentId: 1,
          equipmentName: "设备1",
          eqCode: "1001",
          officeName: "科室1",
          eqType: "分类1"
        },
        {
          equipmentId: 2,
          equipmentName: "设备2",
          eqCode: "1002",
          officeName: "科室2",
          eqType: "分类2"
        },
        {
          equipmentId: 3,
          equipmentName: "设备3",
          eqCode: "1003",
          officeName: "科室3",
          eqType: "分类3"
        }
      ];
      this.total = Number(100);
      this.loading = false;
    }
  }

};
</script>
<style scoped lang="scss">
.box {
  display: flex;
}

.left-class {
  flex: 1;
  margin-right: 20px;
}

.right_content {
  flex: 9;
}
</style>
