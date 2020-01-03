<template>
    <div>
        <el-button round icon="el-icon-edit" size="small" type="success" @click="toAddHandler">添加</el-button>
        <el-button round icon="el-icon-delete" size="small" type="danger">批量删除</el-button>
        <el-table :data="employee">
            <el-table-column prop="id" label="编号"></el-table-column>
            <el-table-column prop="realname" label="真实姓名"></el-table-column>
            <el-table-column prop="name" label="姓名"></el-table-column>
            <el-table-column prop="telephone" label="联系方式"></el-table-column>
            <el-table-column prop="idCard" label="身份证号"></el-table-column>
            <el-table-column prop="bankCard" label="银行卡号"></el-table-column>
            <el-table-column label="操作">
                <template v-slot="slot">
                    <a href="" @click.prevent="toDeleteHandler(slot.row.id)">删除</a>
                    <a href="" @click.prevent="toUpdateHandler(slot.row)">修改</a>
                </template>
            </el-table-column>
        </el-table>
<el-pagination background layout="prev, pager, next"  :total="100"></el-pagination>
        <el-dialog
      title="添加员工信息"
      :visible.sync="visible"
      width="60%">
      <span>这是一段信息</span>
      <span slot="footer" class="dialog-footer">
        <el-button size="small" @click="closeModalHandler">取 消</el-button>
        <el-button size="small" type="primary" @click="closeModalHandler">确 定</el-button>
      </span>
    </el-dialog>
    </div>
</template>
<script>
    export default{
        methods:{
             toDeleteHandler(id){
      this.$confirm('此操作将永久删除该文件, 是否继续?', '提示', {
        confirmButtonText: '确定',
        cancelButtonText: '取消',
        type: 'warning'
      }).then(() => {
        this.$message({
          type: 'success',
          message: '删除成功!'
        });
      })
      
    },
            toAddHandler(){
                this.visible=true;
            },
            closeModalHandler(){
                this.visible=false;
            },
            toUpdateHandler(row){
                this.title="修改员工信息";
                this.visible=true;
            }
        },
    data(){
        return{
            visible:false,
            employee:[{
                id:1,
                realname:"乌拉",
                gender:"男",
                telephone:"33333333",
                idCard:"123456789987",
                bankCard:"00000000000000"
            }]
        }
    },

}
</script>
<style scoped>

</style>