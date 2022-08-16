<template>
  <el-container  class="layout-container-demo">
      <el-header style="text-align: right; font-size: 12px">
          <Head @handleCommand="handleCommand" />
      </el-header>
    <el-container>

    <el-aside width="200px">
        <el-menu v-for="(item,index) in menuItem" :key="index">
              <el-menu-item :index="index">{{item.menuName}}</el-menu-item>
        </el-menu>
    </el-aside>

    <el-container>
      <el-main>
          <el-table :data="tableData">
            <el-table-column prop="date" :label="date" width="140" />
            <el-table-column prop="name" :label="name" width="120" />
            <el-table-column prop="address" :label="address" />
          </el-table>
      </el-main>

      </el-container>

    </el-container>
    <div class="toolbar">
   <el-footer>
    <a href="https://beian.miit.gov.cn/" target="_blank" class="a-link">
      京ICP备19010397号
    </a>
    </el-footer>
    </div>
  </el-container>
</template>

<script>
import Head from './Head.vue'
export default {
  name: 'Home',
  components: {
    Head: Head
  },
  data () {
    return {
      date: '日期',
      name: '姓名',
      address: '地址',
      cnItem: {
        date: '2022-08-11',
        name: '无名氏',
        address: '来无影去无踪'
      },
      enItem: {
        date: '2022-08-11',
        name: 'Who am I',
        address: 'Come without a shadow, go without a trace'
      },
      cnMenuItem: [
        { menuName: '菜单一' },
        { menuName: '菜单二' },
        { menuName: '菜单三' }
      ],
      enMenuItem: [
        { menuName: 'MenuOne' },
        { menuName: 'MenuTwo' },
        { menuName: 'MenuThree' }
      ],
      menuItem: [],
      cnTableData: [],
      enTableData: [],
      tableData: []
    }
  },

  created () {
    this.cnTableData = Array.from({ length: 10 }).fill(this.cnItem)
    this.enTableData = Array.from({ length: 10 }).fill(this.enItem)
    this.tableData = this.cnTableData
    this.menuItem = this.cnMenuItem
  },

  methods: {
    handleCommand (command) {
      if (command === 'cn') {
        this.tableData = this.cnTableData
        this.menuItem = this.cnMenuItem
      } else {
        this.tableData = this.enTableData
        this.menuItem = this.enMenuItem
      }
      this.date = command === 'cn' ? '日期' : 'Date'
      this.name = command === 'cn' ? '姓名' : 'Name'
      this.address = command === 'cn' ? '地址' : 'Address'
    }
  }

}
</script>

<style scoped>
.layout-container-demo .el-header {
  position: relative;
  color: var(--el-text-color-regular);
  font-weight: bold;
  border-bottom: 1px solid #dcdfe6;
}
.layout-container-demo .el-footer {
  color: var(--el-text-color-regular);
  font-weight: bold;
  height: 6vh;
  width: 100%;
  margin-top: 15%;
}

.a-link{
  position: fixed;
  bottom: 45px;
  text-decoration: none;
  color: #aaa;
  font-size: 14px;
}
.layout-container-demo .el-menu {
  border-right: none;
  font-weight: bold;
  color: var(--el-text-color-regular);
}
.layout-container-demo .el-main {
  padding: 0;
  height: 100%;
}
.layout-container-demo .toolbar {
  display: inline-flex;
  align-items: center;
  justify-content: center;
  height: 100%;
  right: 20px;
}
.example-showcase .el-dropdown-link {
  cursor: pointer;
  color: var(--el-color-primary);
  display: flex;
  align-items: center;
}
</style>
