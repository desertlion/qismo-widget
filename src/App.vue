<template lang="pug">
  #qismo-container
    QismoTrigger(:onClickHandler="qismoTriggerHandler" :iconMode="iconMode")
    transition-group(name="slide-vertical" mode="out-in")
      QismoWelcome(v-if="welcomeDialogIsVisible && !loginFormIsVisible" key="qismo-welcome")
      LoginForm(v-if="loginFormIsVisible" key="qismo-login-form")
</template>

<script>
// import posed from 'vue-pose';
// import Comment from './components/Comment.vue';
import QismoTrigger from './components/QismoTrigger.vue';
import LoginForm from './components/LoginForm.vue';
import QismoWelcome from './components/WelcomeWidget.vue';

export default {
  name: 'app',
  components: {
    QismoTrigger,
    LoginForm,
    QismoWelcome,
  },
  data: () => ({
    welcomeDialogIsVisible: false,
    loginFormIsVisible: false,
  }),
  computed: {
    iconMode() { return !this.loginFormIsVisible ? 'open' : 'close'; },
  },
  mounted() {
    setTimeout(() => {
      this.welcomeDialogIsVisible = true;
    }, 300);
  },
  methods: {
    qismoTriggerHandler() {
      this.loginFormIsVisible = !this.loginFormIsVisible;
    },
  },
};
</script>
<style lang="stylus">
.qismo-container *, .qismo-container *:before, .qismo-container *:after {
  box-sizing: border-box;
  margin: 0;
  padding: 0;
}

#qismo-container
  font-family Arial, Helvetica, sans-serif
</style>
