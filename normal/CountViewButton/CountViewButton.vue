<template>
  <div>
 <button class="passwordDialogNumberButton"
                type="button"
                :style="phoneDialogNumberButtonStyle? {color: 'rgba(255, 255, 255, 1)'} : {color: '#989696',fontSize:'14px',background:'#f6f6f6',cursor: 'not-allowed'}"
                @click="changePhoneNumberText(1)">{{phoneDialogNumberText}}</button>
  </div>
</template>

<script>
export default {
  data () {
    return {
      phoneDialogNumberButtonStyle: true
    }
  },
  methods: {
    changePhoneNumberText (type) {
      if (this.phoneDialogNumberText === '发送' && type === 1) {
        this.phoneDialogNumberText = 60

        this.PhoneNumberSet = setInterval(
          () => this.changePhoneNumberText(2),
          1000
        )
        this.phoneDialogNumberButtonStyle = false
      } else if (this.phoneDialogNumberText === 0) {
        clearInterval(this.PhoneNumberSet)
        this.phoneDialogNumberButtonStyle = true
        this.phoneDialogNumberText = '发送'
      } else if (!isNaN(this.phoneDialogNumberText) && type === 2) {
        this.phoneDialogNumberText--
      }
    }
  }
}
</script>

<style lang="stylus" scoped>
.passwordDialogNumberButton {
        width: 60px
        height: 30px
        background: rgba(67, 103, 255, 1)
        border-radius: 2px
        color: rgba(255, 255, 255, 1)
        margin-left: 24px
        outline: none
      }
</style>
