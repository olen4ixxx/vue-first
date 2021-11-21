<template>
  <div class="back">
    <button @click="show = !show">
      Переключить
    </button>
    <transition name="fade">
      <p v-if="show">привет</p>
    </transition>
    <transition name="fade">
      <p v-if="show">привет</p>
    </transition><transition name="fade">
    <p v-if="show">привет</p>
  </transition><transition name="fade">
    <p v-if="show">привет</p>
  </transition><transition name="fade">
    <p v-if="show">привет</p>
  </transition>
    <Loader v-if="loading"/>
  </div>
</template>

<script>
import Vue from "vue";

new Vue({
  el: '#app',
data: {
  show: false
}
})
import Loader from '@/components/Loader'

export default {
  name: 'My',
  data() {
    return {
      show: true,
      loading: true
    }
  },
  mounted() {
      setTimeout(() => {
        this.loading = false
      }, 500)
  },
  components: {
    Loader
  },
  computed: {
    setShow() {
      return !this.show
    }
  }
}
</script>

<style>
.back {
  background: black;
  color: #0ef306;
  font-weight: bold;
}
.fade-enter-active, .fade-leave-active {
  transition: opacity 10s;
}
.fade-enter, .fade-leave-to /* .fade-leave-active до версии 2.1.8 */ {
  opacity: 0;
}
</style>