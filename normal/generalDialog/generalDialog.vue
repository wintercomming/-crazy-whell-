<template>
  <el-dialog
    :visible.sync="dialogVisible"
    :show-close="false"
    class="comfirmUnBindDialog"
    :width="width"
    center
    :close-on-click-modal="false"
    :append-to-body="appendToBody"
  >
  <p class="DialogTitle">{{message}}</p>
  <div @click="closeDialog">
  <svg-icon iconClass="close" class="closeIcon"></svg-icon>
  </div>
  <slot>

  </slot>
  </el-dialog>

</template>

<script>
export default {
  props: {
    message: {
      type: String,
      default: ''
    },
    width: {
      type: String,
      default: '800px'
    },
    appendToBody: {
      type: Boolean,
      default: false
    },
    dialogVisible: Boolean
  },

  data () {
    return {

    }
  },

  methods: {
    closeDialog () {
      this.$emit('cancelDialog')
    }
  }
}
</script>

<style lang="stylus" scoped>
.DialogTitle{
    float:left;
    margin-top:-37px;
    font-weight:500;
    color:rgba(51,51,51,1);
    font-size:16px;
    font-family:SourceHanSansSC-Medium;
}
.closeIcon{
    float:right;
    margin-top:-45px;
    margin-right:-15px;
    width:20px;
    height:20px;
    cursor:pointer
  }
</style>
