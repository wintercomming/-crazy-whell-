<template>
  <el-dialog
    :visible.sync="dialogVisible"

    class="comfirmUnBindDialog"
    width="800px"
    :close-on-click-modal="false"
    center
    @close = "handleClose"
  >
  <div @click="cancel">
  <!-- <svg-icon iconClass="close" class="closeIcon"></svg-icon> -->
  </div>
    <!-- :before-close="handleClose" -->
    <p class="comfirmUnBindDialogText">{{message}}</p>
    <span slot="footer">
      <el-button @click="cancel" class="comfirmUnBindDialogCancelButton">取消</el-button>
      <el-button type="primary" @click="confirm" class="comfirmUnBindDialogConfirmButton">确定</el-button>
    </span>
  </el-dialog>
</template>

<script>
/**
 * @author yaomingjie
 * @date 2019 05 31
 * @description 一类弹窗组件
 * TODO:
 * 使用说明:
 * 使用时需传入message参数,代表弹窗中间所显示的文字内容。
 */
export default {
  props: {
    message: {
      type: String,
      default: ''
    }
    // dialogVisible: Boolean
    // dialogVisible: this.params.dialogVisible
  },
  data () {
    return {
      dialogVisible: false
    }
  },
  methods: {
    show () {
      this.dialogVisible = true
    },
    hide () {
      this.dialogVisible = false
    },
    handleClose () {
      this.$emit('cancel')
    },
    confirm () {
      this.$emit('confirm')
    },
    cancel () {
      this.$emit('cancel')
    }
  },
  mounted () {

  }
}
</script>

<style lang="stylus" scoped>
.comfirmUnBindDialog {
  text-align: center;

  .comfirmUnBindDialogText {
    text-align: center;
    font-size: 18px;
    font-family: SourceHanSansSC-Normal;
    font-weight: 400;
    color: rgba(102, 102, 102, 1);
    margin-top: 61px;
  }

  .comfirmUnBindDialogCancelButton {
    width: 120px;
    height: 40px;
    border: 1px solid rgba(229, 231, 236, 1);
    border-radius: 4px;
    margin-top: 78px;
    color: rgba(119, 119, 119, 1);
  }

  .comfirmUnBindDialogConfirmButton {
    width: 120px;
    height: 40px;
    background: rgba(67, 103, 255, 1);
    margin-top: 78px;
    border-radius: 4px;
    margin-left: 100px;
  }

  .closeIcon{
    float:right;
    margin-top:-43px;
    margin-right:-15px;
    width:20px;
    height:20px;
    cursor:pointer
  }

}
</style>
