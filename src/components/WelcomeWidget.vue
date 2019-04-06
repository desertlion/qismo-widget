<template lang="pug">
    .qismo-welcome
        transition-group(name="slide-vertical" mode="out-in")
            .qismo-welcome__dialog(key="welcome-dialog" v-if="welcomeDialogIsActive")
                img.qismo-welcome__close-btn(src="../assets/img/close-circle.svg" @click="welcomeDialogIsActive = false")
                .qismo-welcome__dialog-header
                    .qismo-welcome__dialog-avatar
                        img(src="../assets/img/qiscus-logo.png")
                    strong Qiscus Support
                .qismo-welcome__dialog-body
                    p Hi there! Do you want to have a chat widget like this? It's so easy and customisable! So, come on have a chat with us!

            //- start Attention Grabber
            .qismo-attention-grabber(key="attention-grabber" v-if="attentionGrabberIsActive")
                img.qismo-attention-grabber__close-btn(src="../assets/img/close-circle.png" @click="attentionGrabberIsActive = false")
                .qismo-attention-grabber__img(:style="grabberStyle")
                .qismo-attention-grabber__txt Hello there, we have a promo here, check it out <a href="#">link</a>
</template>

<script>
export default {
  name: 'QismoWelcome',
  data: () => ({
    welcomeDialogIsActive: false,
    attentionGrabberIsActive: false,
    grabberStyle: `background: url(${require('../assets/img/att-grabber-sample-img.png')}) no-repeat center`,
  }),
  mounted() {
    setTimeout(() => {
      this.welcomeDialogIsActive = true;
    }, 150);
    setTimeout(() => {
      this.attentionGrabberIsActive = true;
    }, 250);
  },
};
</script>

<style lang="stylus">
.qismo-welcome
    width 360px
    position fixed
    bottom 85px
    right 25px
    display flex
    flex-direction column
.qismo-welcome__dialog
    background #FFF
    border-radius 8px
    box-shadow 0px 8px 24px rgba(51, 51, 51, 0.1)
    text-align center
    padding 32px
    position relative
    & .qismo-welcome__dialog-avatar img
        background linear-gradient(270deg, #74C162 -0.04%, #55BD97 100%)
        border-radius 50%
        width 54px
        height 54px
        position absolute
        top 0
        left 50%
        transform translate(-50%, -50%)
    strong
        font-weight bold
        font-size 18px
        margin 12px auto 24px auto
        display block
    p
        line-height 1.7em
        font-size 14px
    & .qismo-welcome__close-btn
        position absolute
        top -25px
        right 0
        width 24px
        height 24px
        cursor pointer
.qismo-attention-grabber
    background #FFF
    border-radius 8px
    box-shadow 0px 8px 24px rgba(51, 51, 51, 0.1)
    margin-top 15px
    padding 0
    position relative
.qismo-attention-grabber__close-btn
    position absolute
    top 16px
    right 16px
    cursor pointer
.qismo-attention-grabber__img
    background-size cover
    width 360px
    height 180px
.qismo-attention-grabber__txt
    padding 15px 32px
    text-align center
.slide-vertical-enter, .slide-vertical-leave-to
    opacity 0
    transform scale(0.9) translateY(130px)
.slide-vertical-enter-to
    opacity 1
    transform scale(1) translateY(0)
.slide-vertical-enter-active, .slide-vertical-leave-active
    transition all 0.32s ease
</style>
