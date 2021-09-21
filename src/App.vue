<template>
  <div class='main'>
    <button @click="myAnimation ='slide'">Slide</button>
    <button @click="myAnimation ='fade'">Fade</button>
    <p>{{ myAnimation }}</p>
    <button @click='show = !show'>切り替え</button>
    <transition name='fade'>
      <p
        v-if='show'
        key='bye'
      >さよなら</p>
      <p
        v-else
        key='hello'
      >こんにちは</p>
    </transition>
    <transition
      enter-active-class='animate__animated animate__bounce'
      enter-to-class=''
      leave-active-class='animate__animated animate__shakeX'
      leave-to-class=''
      appear
    >
      // name部分の文字がstyleと連携する
      // name:なし v-enter/v-leave
      // name:fade fade-enter/fade-leave
      // name:xxx xxx-endter/xxx-leave
      <p v-if='show'>hello</p>
    </transition>

    <transition
      :name='myAnimation'
      appear
    >
        <p v-show='show'>bye</p>
    </transition>
  </div>
</template>

<script>
export default {
  data() {
    return {
      show: true,
      myAnimation: 'slide'
    };
  }
};
</script>

<style scoped>
.fade-enter {
/* 現れる時の最初の状態 */
  opacity: 0;
}
.fade-enter-active {
/* 現れる時のトランジションの状態 */
  transition: opacity 3s;
}
.fade-enter-to {
/* 現れる時の最後の状態 */
  opacity: 1;
}
.fade-leave {
/* 消える時の最初の状態 */
  opacity: 1;
}
.fade-leave-active {
/* 消える時のトランジションの状態 */
  transition: opacity 4s;
}
.fade-leave-to {
/* 消える時の最後の状態 */
  opacity: 0;
}

.slide-enter,
.slide-leave-to {
  opacity: 0;
}
.slide-enter-active {
  animation: slide-in 0.5s;
  transition: opacity 5s;
}
.slide-enter-to {}
.slide-leave {}
.slide-leave-active {
  animation: slide-in 0.5s reverse;
  transition: opacity 5s;
}
.slide-leave-to {}

@keyframes slide-in {
  from {
    transform: translateX(100px);
  }
  to {
    transform: translateX(0);
  }
}

.main {
  width: 70%;
  margin: auto;
  padding-top: 5rem;
  text-align: center;
}
</style>