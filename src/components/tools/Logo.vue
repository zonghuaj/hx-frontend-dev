<template>
  <div class="logo">
    <router-link :to="{name:'dashboard'}">
      <!--LogoSvg alt="logo" /-->
      <div class="hx-header-logo"></div>
      <h1 v-if="showTitle"></h1>
    </router-link>
  </div>
</template>

<script>
// import LogoSvg from '@/assets/logo.svg?inline';

export default {
  name: 'Logo',
  components: {
    // LogoSvg
  },
  props: {
    title: {
      type: String,
      default: 'Ant Design Pro',
      required: false
    },
    showTitle: {
      type: Boolean,
      default: true,
      required: false
    }
  }
};
</script>

<style scoped>
  .hx-header-logo {
      position: absolute;
      left: 0;
      height: 100%;
      background: url(../../assets/hx-logo.png) no-repeat center;
      background-size: 100%;
      width: 162px;
      margin-left: 25px;
  }
</style>
