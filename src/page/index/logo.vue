<template>
  <div class="avue-logo">
    <transition name="fade">
      <span
        v-if="keyCollapse"
        key="0"
        class="avue-logo_subtitle">
        {{ website.logo }}
      </span>
    </transition>
    <transition-group name="fade">
      <template v-if="!keyCollapse">
        <span
          key="1"
          class="avue-logo_title" @click="goIndex">{{ website.indexTitle }} </span>
      </template>
    </transition-group>
  </div>
</template>

<script>
import { mapGetters } from 'vuex'
export default {
  name: 'Logo',
  computed: {
    ...mapGetters(['website', 'keyCollapse'])
  },
  methods: {
    goIndex: function () {
      window.location.reload()
    }
  }
}
</script>

<style lang="scss">
    .avue-logo_title {
        cursor: pointer;
    }
.fade-leave-active {
  transition: opacity 0.2s;
}
.fade-enter-active {
  transition: opacity 2.5s;
}
.fade-enter,
.fade-leave-to {
  opacity: 0;
}
.avue-logo {
  position: fixed;
  top: 0;
  left: 0;
  width: 240px;
  height: 64px;
  line-height: 64px;
  background-color: #20222a;
  font-size: 20px;
  overflow: hidden;
  box-sizing: border-box;
  box-shadow: 0 1px 2px 0 rgba(0, 0, 0, 0.15);
  color: rgba(255, 255, 255, 0.8);
  z-index: 1024;
  &_title {
    display: block;
    text-align: center;
    font-weight: 300;
    font-size: 16px;
  }
  &_subtitle {
    display: block;
    text-align: center;
    font-size: 18px;
    font-weight: bold;
    color: #fff;
  }
}
</style>
