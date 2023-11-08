<template>
  <div :class="classObj" class="app-wrapper">
    <app-main />
  </div>
</template>

<script>
import { AppMain } from './components'

export default {
  name: 'Layout',
  components: {
    AppMain
  },
  computed: {
    sidebar() {
      return this.$store.state.app.sidebar
    },
    classObj() {
      return {
        hideSidebar: !this.sidebar.opened,
        openSidebar: this.sidebar.opened,
        withoutAnimation: this.sidebar.withoutAnimation
      }
    }
  },
  methods: {
    handleClickOutside() {
      this.$store.dispatch('app/closeSideBar', { withoutAnimation: false })
    }
  }
}
</script>

<style lang="scss" scoped>
  @import "~@/styles/mixin.scss";
  @import "~@/styles/variables.scss";

  .app-wrapper {
    @include clearfix;
    position: relative;
    height: 100%;
    width: 100%;
    background: #F1F2F4;
    // &.mobile.openSidebar{
    //   position: fixed;
    //   top: 0;
    // }
  }
  .drawer-bg {
    background: #000;
    opacity: 0.3;
    width: 100%;
    top: 0;
    height: 100%;
    position: absolute;
    z-index: 999;
  }
  //   .mobile .fixed-header {
  //   width: 100%;
  // }
  .main-container {
    background: #F1F2F4;
  }
  //样式修改
  .sidebar-container{
    background: #ffffff !important;
  }
  ::v-deep .el-menu {
    border: none;
    height: 100%;
    width: 100% !important;
    // background-color: #ffffff !important;
  }
  ::v-deep .el-menu-item {
    background-color: #ffffff !important;
    color: #636E95 !important;
    padding-left: 60px !important;
  }
  ::v-deep .submenu-title-noDropdown {
    padding-left: 20px !important;
  }
  ::v-deep  .el-submenu__title {
    background-color: #ffffff !important;
    color: #636E95 !important;
  }
  ::v-deep .el-menu-item  {
    &.is-active{
      color: #0049FF !important;
      background-color: #F2F6FF !important;
    }
    // padding-left: 40px !important;
  }
  ::v-deep .svg-icon {
    font-size: 18px !important;
  }
</style>
