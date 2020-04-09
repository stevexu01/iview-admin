<template>
  <Row :gutter="10">
    <i-col span="6">
      <Card>
        <Upload action="" :before-upload="beforeUpload">
          <Button icon="ios-cloud-upload-outline">Upload CSV</Button>
          &nbsp;&nbsp;&nbsp;&nbsp;CLick to Upload
        </Upload>
        <p>util.js：</p>
        <p class="update-table-intro"><Icon style="margin-right: 10px;" :size="10" type="md-heart"/><span class="code-high-line">getArrayFromFile</span>：CSV to datatable</p>
        <p class="update-table-intro"><Icon style="margin-right: 10px;" :size="10" type="md-heart"/><span class="code-high-line">getTableDataFromArray</span>：CSV to datatable</p>
      </Card>
    </i-col>
    <i-col span="18">
      <Table :height="500" :columns="columns" :data="tableData"/>
    </i-col>
  </Row>
</template>

<script>
import { getArrayFromFile, getTableDataFromArray } from '@/libs/util'
export default {
  name: 'update_table_page',
  data () {
    return {
      columns: [],
      tableData: []
    }
  },
  methods: {
    beforeUpload (file) {
      getArrayFromFile(file).then(data => {
        let { columns, tableData } = getTableDataFromArray(data)
        this.columns = columns
        this.tableData = tableData
      }).catch(() => {
        this.$Notice.warning({
          title: '只能上传Csv文件',
          desc: '只能上传Csv文件，请重新上传'
        })
      })
      return false
    }
  }
}
</script>

<style>
.update-table-intro{
  margin-top: 10px;
}
.code-high-line{
  color: #2d8cf0;
}
</style>
