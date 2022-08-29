<template>
    <el-menu v-for="(item,index) in menuItem" :key="index">
          <el-menu-item :index="index">{{item.menuName}}</el-menu-item>
    </el-menu>
</template>
<script>

export default {
  name: 'Menu',
  data () {
    return {
      cnMenuItem: [
        { menuName: 'MD基本操作' },
        { menuName: '菜单二' },
        { menuName: '菜单三' }
      ],
      enMenuItem: [
        { menuName: 'MD base operation' },
        { menuName: 'MenuTwo' },
        { menuName: 'MenuThree' }
      ],
      menuItem: []
    }
  },

  created () {
    this.menuItem = this.cnMenuItem
  },

  methods: {
    handleCommand (command) {
      if (command === 'cn') {
        this.menuItem = this.cnMenuItem
      } else {
        this.menuItem = this.enMenuItem
      }
    }
  }
}
</script>
