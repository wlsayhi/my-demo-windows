
<template>
  <div class="my-home">
    <el-dialog  v-dialogDrag title="提示" :visible.sync="dialogVisible" :modal="false" :close-on-click-modal="false" :modal-append-to-body="false" width="30%">
      <span>我的中心</span>
      <span slot="footer" class="dialog-footer">
      </span>
    </el-dialog>
  </div>
</template>
<script>
export default {
  data() {
    return {
      dialogVisible: false
    };
  },
  props: ['index','businessName'],
  watch: {
    businessName(val) {
      if (val == '个人中心') {
          this.dialogVisible = true;
      }
    }
  },
};
</script>
<style lang="scss">
  .my-home {
    z-index: 99;
  }
  .el-dialog__wrapper {  //蒙版
    pointer-events:none; // 使蒙版穿透可以点击蒙版下面的事件 但是蒙版子元素事件会失效

    .el-dialog {     //弹窗
      pointer-events: auto;  //使弹窗事件有效
    }
  }
</style>