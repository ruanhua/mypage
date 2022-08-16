<template>
    <div class="toolbar">
        <el-dropdown trigger="click" @command="handleCommand">
            <span class="el-dropdown-link">
                语言/Language
                <el-icon class="el-icon--right">
                <arrow-down />
                </el-icon>
            </span>
        <template #dropdown>
            <el-dropdown-menu>
            <el-dropdown-item command="cn">中文简体</el-dropdown-item>
            <el-dropdown-item command="en">English</el-dropdown-item>
            </el-dropdown-menu>
        </template>
        </el-dropdown>
    </div>
</template>
<script>

export default {
  name: 'Head',
  methods: {
    handleCommand (command) {
      this.$emit('handleCommand', command)
    }
  }

}
</script>
