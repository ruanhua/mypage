<template>
  <el-container  class="layout-container-demo">
      <el-header style="text-align: right; font-size: 12px">
          <Head @handleCommand="handleCommand" />
      </el-header>
    <el-container>

    <el-aside width="200px">
          <Menu ref="menu" @showContent="showContent" />
    </el-aside>

    <el-container>
      <el-main>
        <Main ref="main"/>
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
import Menu from './Menu.vue'
import Main from './Main.vue'
export default {
  name: 'Home',
  components: {
    Head: Head,
    Menu: Menu,
    Main: Main
  },
  methods: {
    handleCommand (command) {
      this.$refs.menu.handleCommand(command)
      this.$refs.main.handleCommand(command)
    },
    showContent (id) {
      this.$refs.main.handleCommandDesc(id)
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
  text-align: center;
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

.layout-container-demo .toolbar {
  display: inline-flex;
  align-items: center;
  justify-content: center;
  height: 100%;
  right: 20px;
}
</style>
