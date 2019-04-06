<template lang="pug">
    .qismo-trigger
        button(@click="onClickHandler")
            img.qismo-trigger__icon(src="../assets/img/icon-qiscus-widget-default.png" v-if="iconMode == 'open'")
            img.qismo-trigger__icon(src="../assets/img/ic_cancel.png" v-if="iconMode == 'close'")
            .qismo-trigger__text(v-if="iconMode == 'open'") Talk to Us
</template>

<script>
export default {
  name: 'QismoTrigger',
  props: ['onClickHandler', 'iconMode'],
};
</script>

<style lang="stylus">
.qismo-trigger
    position fixed
    bottom 15px
    right 25px
.qismo-trigger button
    border 0
    border-radius 30px
    display flex
    justify-content space-between
    align-items center
    padding 15px
    color #FFF
    background #55BD97
    cursor pointer
    outline none
    &:hover .qismo-trigger__icon
        transform rotate(360deg)
    &:hover .qismo-trigger__text
        width auto
        height auto
        margin-left 15px
        transform translateX(0)
.qismo-trigger__icon
    transition transform .32s ease-in-out
.qismo-trigger__text
    width 0
    height 0
    overflow hidden
    transform translateX(30px)
    transition all .32s ease
@keyframes rotate-center {
    0% { transform: rotate(0); }
    100% { transform: rotate(360deg); }
}
</style>
