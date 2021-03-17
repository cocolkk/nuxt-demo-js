<template>
    <div>
        <div class="search-condition">
            <el-input v-model="filter" style="width: 300px;"></el-input>
            <el-button type="primary">搜索</el-button>
        </div>
        <el-table :data="tableData" border>
            <el-table-column prop="paperNo" label="试卷编码"></el-table-column>
            <el-table-column label="标题"></el-table-column>
            <el-table-column label="题号"></el-table-column>
            <el-table-column label="题目"></el-table-column>
            <el-table-column label="题目图片"></el-table-column>
            <el-table-column label="操作">
                <template slot-scope="scope">
                    <el-button type="text" @click="eidtOpt(scope.row)">编辑</el-button>
                    <el-button type="text" @click="deleteOpt(scope.row)">删除</el-button>
                </template>
            </el-table-column>
        </el-table>
        <el-dialog :visible.sync="dialogEdit" title="编辑题目/选项">
        <el-form :model="formData" label-width="120px">
            <el-form-item label="题目编号">{{titleNum}}</el-form-item>
            <el-form-item label="题目名称">
                <el-input v-model="formData.title"></el-input>
            </el-form-item>
            <el-form-item label="题目图片">
                <el-upload action="#" list-type="picture-card"></el-upload>
            </el-form-item>
            <el-tabs v-model="editableTabsValue" type="card" @edit="handleTabsEdit">
                <el-tab-pane
                    :key="item.name"
                    v-for="(item, index) in editableTabs"
                    :label="item.title"
                    :name="item.name">
                    {{item.content}}
                </el-tab-pane>
            </el-tabs>
            <div>
                <el-form-item label="选项A:">
                    <el-input></el-input>
                </el-form-item>
                <el-form-item label="分数A:">
                    <el-input></el-input>
                </el-form-item>
                <el-form-item label="选项A类型:">
                    <el-input></el-input>
                </el-form-item>
                <el-form-item label="选项A图片:">
                    <!-- <el-upload> -->
                        <!-- <i class="icon"></i> -->
                        <!-- <el-button type="primary">添加图片</el-button> -->
                    <!-- </el-upload> -->
                </el-form-item>
                <el-form-item label="选项A跳转题号:">
                    <el-input></el-input>
                </el-form-item>
            </div>
        </el-form>
        <div class="center-btn">
            <el-button type="primary" @click="submitBtn">提交</el-button>
        </div>
        </el-dialog>
    </div>
</template>

<script>
export default {
    data() {
        return {
            dialogEdit: false,
            titleNum: '000000000',
            filter: '',
            formData: {
                title: '',
                img: ''
            },
            tableData: [{paperNo: '111111'}],
            editableTabsValue: '2',
            editableTabs: [
              {
                title: '选项A',
                name: 'A',
                content: 'Tab A content'
              },
              {
                title: '选项B',
                name: 'B',
                content: 'Tab B content'
              },
              {
                title: '选项C',
                name: 'C',
                content: 'Tab C content'
              },
              {
                title: '选项D',
                name: 'D',
                content: 'Tab D content'
              }],
              tabIndex: 2
         }
    },

    mounted() {

    },

    methods: {
        // 编辑操作
        eidtOpt() {
            this.dialogEdit = true;
        },

        // 编辑提交
        submitBtn() {
            if(this.formData.title === '' && this.formData.img === ''){
              this.$message({
                type: 'error',
                message: '题目和图片至少填写一项'
              })
              return
            }
        },

        handleTabsEdit(){},

        // 删除操作
        deleteOpt() {

        }
    }

}
</script>

<style scoped>
.search-condition {
    display: flex;
    padding: 10px 0;
}
.center-btn {
    display: flex;
    justify-content: center;
}
</style>
