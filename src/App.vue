<!--<template>-->
  <!--<div id="app">-->
    <!--<h1>{{title}}</h1>-->
    <!--<v-button status="primary">Hi</v-button>-->
    <!--<v-table :data="data">-->
      <!--<v-table-column v-for="column in headers" :key="column.header"-->
        <!--:label="column.header" :column-key="column.source"-->
        <!--&gt;</v-table-column>-->
    <!--</v-table>-->

  <!--</div>-->
<!--</template>-->

<!--<script>-->

  <!--export default {-->
    <!--name: 'app',-->
    <!--data () {-->
        <!--return {-->
          <!--// 填入管理端标题-->
          <!--title: '标签管理后台',-->
          <!--// 填入表格头-->
          <!--headers: [-->
            <!--{ header: '标签名', type: 'editable', source: 'name'},-->
            <!--{ header: '关键字', type: 'editable', source: 'keyword'},-->
            <!--{ header: '日期', type: 'editable', source: 'date'}-->
          <!--],-->
          <!--data: [-->
            <!--{name: '1', keyword: '1', date: '1'}-->
          <!--]-->
        <!--}-->
    <!--}-->
  <!--}-->
<!--</script>-->

<!--<style>-->
<!--#app {-->
  <!--font-family: 'Avenir', Helvetica, Arial, sans-serif;-->
  <!-- -webkit-font-smoothing: antialiased;-->
  <!-- -moz-osx-font-smoothing: grayscale;-->
  <!--color: #2c3e50;-->
  <!--margin-top: 20px;-->
  <!--display: flex;-->
  <!--flex-direction: column;-->
  <!--align-items: center;-->
<!--}-->
<!--</style>-->

<template>
  <div>
    <h1>H</h1>
    <v-button status="primary">Hi</v-button>
  <v-table
    :data="data1">
    <v-table-column v-for="column in columns1" :key="column.label"
                    :column-key="column.columnKey"
                    :label="column.label"
                    :align="column.align"
                    :sortable="column.sortable"
                    :width="column.width"
                    :formatter="column.formatter"
    ></v-table-column>
    <v-table-column align="right">
      <template slot="cell" scope="props">
        <a @click.stop="deleteRow(props.index)" class="table-delete">删除</a>
      </template>
    </v-table-column>
  </v-table>
  </div>
 </template>

<script>
  const data = [];
  for (let i = 0; i < 10; ++i) {
    data.push({
      name: 'erwin',
      date: +new Date(),
      math: parseInt(Math.random() * 100),
      english: parseInt(Math.random() * 100),
      cpp: parseInt(Math.random() * 100),
      sql: parseInt(Math.random() * 100)
    });
  }

  const columns = [{
    label: '姓名',
    columnKey: 'name',
    width: 200,
    expandable: true
  },
    {
      label: '日期',
      columnKey: 'date',
      sortable: true,
      formatter: function (value) {
        return new Date(value).toString().substr(0, 15);
      }
    },
    {
      label: '数学',
      columnKey: 'math',
      align: 'right',
      width: 100
    },
    {
      label: '英语',
      columnKey: 'english',
      align: 'right',
      sortable: true,
      width: 100
    },
    {
      label: 'C++',
      columnKey: 'cpp',
      align: 'right',
      width: 100
    }]

  export default {
    data() {
      return {
        columns1: columns,
        data1: data,
      };
    },
    methods: {
      deleteRow(index) {
        console.log(index);
        this.data1.splice(index, 1);
      }
    }
  }
</script>
