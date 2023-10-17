<template>
  <div class="type_left">
    <el-tabs>
      <el-tab-pane label="设备分类">
        <div class="scroll">
          <el-tree :data="typeList" node-key="typeId" check-on-click-node check-strictly
                   :expand-on-click-node="false" :highlight-current="true">
            <span class="custom-tree-node" slot-scope="{ node, data }"
                  :class="{ highlight: data.typeId === selectedId }">
              <span :title="data.typeName + '(' + data.eqNumber + ')'">{{
                  data.typeName + '(' + data.eqNumber + ')'
                }}</span>
            </span>
          </el-tree>
        </div>
      </el-tab-pane>
      <el-tab-pane label="科室列表">
        <el-tree :data="officeList" node-key="typeId" check-on-click-node check-strictly
                 :expand-on-click-node="false" :highlight-current="true">
            <span class="custom-tree-node" slot-scope="{ node, data }"
                  :class="{ highlight: data.officeId === selectedId }">
              <span :title="data.officeName + '(' + data.eqNumber + ')'">{{
                  data.officeName + '(' + data.eqNumber + ')'
                }}</span>
            </span>
        </el-tree>
      </el-tab-pane>
    </el-tabs>
  </div>
</template>
<script>
export default {
  name: "",
  data() {
    return {
      // 选中的分类id数组
      selectedId: [],
      // 分类列表
      typeList: [],
      // 科室列表
      officeList:[],
    }
  },
  created() {
    // 初始化分类列表
    this.getTypeList();
    // 初始化科室列表
    this.getOfficeList();
  },
  methods: {
    // 查询分类列表
    getTypeList() {
      this.typeList = [
        {
          typeId: 1001,
          typeName: "分类1",
          eqNumber: 1
        },
        {
          typeId: 1002,
          typeName: "分类2",
          eqNumber: 1
        },
        {
          typeId: 1003,
          typeName: "分类3",
          eqNumber: 1
        }
      ]
    },
    // 查询科室列表
    getOfficeList() {
      this.officeList = [
        {
          officeId: 1001,
          officeName: "科室1",
          eqNumber: 1
        },
        {
          officeId: 1002,
          officeName: "科室2",
          eqNumber: 1
        },
        {
          officeId: 1003,
          officeName: "科室3",
          eqNumber: 1
        }
      ]
    },
  }
}
</script>


<style scoped lang="scss">

</style>
