<template lang="pug">
    .qismo-login-form
        .qismo-login-form__header
            img(src="../assets/img/qiscus-logo.png" width="24")
            h3 Hi, Welcome to Qiscus!
            p Please fill the details bleow before start chatting with us.
        .qismo-login-form__body
            div.qismo-input
                .icon
                    img(src="../assets/img/ic_contact.png")
                input(type="text" placeholder="Type your name")
            div.qismo-input
                .icon
                    img(src="../assets/img/ic_email.png")
                input(type="text" placeholder="Type your email address")
            button.qismo-login-btn Start Chatting
</template>

<script>
export default {
  name: 'LoginForm',
};
</script>

<style lang="stylus">
.qismo-login-form
    position fixed
    width 360px
    background #FFF
    border-radius 8px
    box-shadow: 0px 20px 35px rgba(189, 189, 189, 0.24);
    bottom 90px
    right 25px
    overflow hidden
.qismo-login-form__header
    padding 36px
    color #FFF
    background #55BD97
    img
        width 24px
        height 24px
        margin-bottom 36px
    h3
        font-weight bold
        font-size 24px
        margin-bottom 16px
    p
        line-height 25px
        font-size 14px
.qismo-login-form__body
    padding 36px
.qismo-input
    background #FFF
    box-shadow 0px 16px 32px rgba(95, 169, 142, 0.12)
    border-radius 6px
    display flex
    overflow hidden
    margin-bottom 32px
    input
        flex 1
        border 0
        padding 10px
        outline none
    & .icon
        background #55BD97
        width 48px
        height 48px
        display flex
        justify-content center
        align-items center
.qismo-login-btn
    background #55BD97
    border-radius 30px
    padding 14px 22px
    border 0
    color #FFF
    display block
    margin 15px auto 0 auto
    cursor pointer
    transition transform .32s ease
    &:hover
        transform translateY(-3px)
</style>
