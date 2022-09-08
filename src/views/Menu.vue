<template>
    <el-menu v-for="(item,index) in menuItem" :key="index">
          <el-menu-item :index="index" @click="getMenuId(item.menuId)">{{item.menuName}}</el-menu-item>
    </el-menu>
</template>
<script>

export default {
  name: 'Menu',
  data () {
    return {
      cnMenuItem: [
        { menuId: 1, menuName: 'MD基本操作' },
        { menuId: 2, menuName: '数组为啥从0开始' },
        { menuId: 3, menuName: '菜单三' }
      ],
      enMenuItem: [
        { menuId: 4, menuName: 'MD base operation' },
        { menuId: 5, menuName: 'Why array start zero' },
        { menuId: 6, menuName: 'MenuThree' }
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
    },
    getMenuId (id) {
      // eslint-disable-next-line no-debugger
      debugger
      this.$emit('showContent', id)
    }
  }
}
</script>
