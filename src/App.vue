<template>
  <div>
    <vxe-virtual-tree
      resizable
      show-overflow
      show-header-overflow
      row-key
      ref="xVTree"
      height="500"
      :tree-config="{ children: 'children' }"
      :columns="tableColumn"
      :data="tableData"
      :border="true"
    >
    </vxe-virtual-tree>
  </div>
</template>

<script>
import { data } from "./data";
import { projectDataColumn } from "./projectData";
export default {
  data() {
    return {
      tableColumn: [
        {
          title: "部门",
          field: "department_name",
          width: 250,
          fixed: "left",
          slots: {
            default: ({ row }) => {
              return [
                <div
                  onClick={() => {
                    const xVTree = this.$refs.xVTree;
                    row.children = [...row.children];
                    xVTree.setTreeExpand([row], true);
                  }}
                >
                  {row.department_name}
                </div>,
              ];
            },
          },
        },
        {
          title: "项目名称",
          field: "project_name",
          width: 250,
        },
        {
          title: "费用说明",
          field: "desc",
          width: 250,
        },
        {
          title: "预算编码",
          field: "budget_code",
          width: 250,
        },
        {
          title: "项目负责人",
          field: "project_admin_id",
          width: 250,
        },
        {
          title: "控制周期",
          field: "control_cycle",
          width: 250,
        },
        {
          title: "资产类别",
          field: "asset_type_code",
          width: 250,
        },
        {
          title: "资产名称",
          field: "asset_name",
          width: 250,
        },
        {
          title: "预计终验时间",
          field: "asset_accepted_at",
          width: 250,
        },
        ...projectDataColumn
      ],
      tableData: data,
    };
  },
  mounted() {
    console.log(this.tableColumn);
  },
};
</script>