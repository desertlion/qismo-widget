<template>
    <Parent class="qcw-comment">
        <div class="qcw-comment__dots" @click="toggleInfo">
            <div class="dot"></div>
            <div class="dot"></div>
            <div class="dot"></div>
        </div>
        <PoseTransition>
            <Info class="qcw-comment__info" v-if="shown" :class="infoClass">
                <li>menu 1</li>
                <li>menu 2</li>
                <li>menu 3</li>
            </Info>
        </PoseTransition>
    </Parent>
</template>

<script>
import posed, { PoseTransition } from 'vue-pose';

export default {
  name: 'Comment',
  components: {
    PoseTransition,
    Parent: posed.li({
      visible: { opacity: 1, y: 0 },
      hidden: { opacity: 0, y: 20 },
    }),
    Info: posed.ul({
      enter: { opacity: 1, y: 0 },
      exit: { opacity: 0, y: 20 },
    }),
  },
  data: () => ({
    shown: false,
    infoClass: 'qcw-comment__info--bottom',
  }),
  mounted() {
    console.log(this.shown);
  },
  methods: {
    toggleInfo(e) {
      // calculate position
      const parent = document.querySelector('.qcw-comment-list');
      const parentScrollHeight = parent.scrollHeight - 30;
      if (e.clientY >= parentScrollHeight) {
        this.infoClass = 'qcw-comment__info--top';
      } else {
        this.infoClass = 'qcw-comment__info--bottom';
      }
      this.shown = !this.shown;
    },
  },
};
</script>

<style lang="stylus">
.qcw-comment {
  width: 100%;
  height: 50px;
  border-radius: 5px;
  background: #fff;
  margin-bottom: 10px;
  position relative
}
.qcw-comment__dots {
    width: 40px;
    height: 10px;
    position: absolute;
    top: 10px;
    right: 10px;
    display: flex;
    justify-content: space-between;
    transform scale(.5)
    cursor pointer
}
.dot{
    background: #444;
    border-radius: 50%;
    width: 10px;
    height: 10px;
}
.qcw-comment__info
  list-style none
  background rgba(0,0,0,.7)
  color #ffffff
  line-height 1.7em
  padding 5px 15px
  border-radius 5px
  position absolute
  right 15px
  z-index 200
.qcw-comment__info--top
    top -100%px
.qcw-comment__info--bottom
    top 25px
</style>
