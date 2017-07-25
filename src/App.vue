<template>
  <div id="app">
    <h1>{{title}}</h1>
    <v-table :data="data" :pagination="pagination">
      <v-table-column v-for="column in headers" :key="column.header"
        :label="column.header" :column-key="column.source"
        ></v-table-column>
    </v-table>
  </div>
</template>

<script>
  import VTable from "../node_modules/vhtml-ui/packages/table/src/table";
  import VTableColumn from "../node_modules/vhtml-ui/packages/table/src/table-column";

  export default {
    components: {VTableColumn, VTable, VButton},
    name: 'app',
    data () {
        return {
          // 填入管理端标题
          title: '标签管理后台',
          // 填入表格头
          headers: [
            { header: '标签名', type: 'editable', source: 'name'},
            { header: '关键字', type: 'editable', source: 'keyword'},
            { header: '日期', type: 'editable', source: 'date'}
          ],
          data: [
            {name: '1', keyword: '1', date: '1'}
          ]
        }
    }
  }
</script>

<style>
#app {
  font-family: 'Avenir', Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  color: #2c3e50;
  margin-top: 20px;
  display: flex;
  flex-direction: column;
  align-items: center;
}
</style>
