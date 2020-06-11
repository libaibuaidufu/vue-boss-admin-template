<template>
  <div class="admin-container" :class="classObj">
    <sidebar />
    <div class="admin-main">
      <navbar />
      <app-main />
    </div>
  </div>
</template>

<script>
import { Navbar, AppMain, Sidebar } from "./components";
export default {
  name: "Layout",
  components: {
    Navbar,
    AppMain,
    Sidebar,
  },
  computed: {
    classObj() {
      console.log(this.$store.state.app.sidebar.opened)
      return {
        hideSidebar: !this.$store.state.app.sidebar.opened,
        openSidebar: this.$store.state.app.sidebar.opened,
      };
    },
  },
};
</script>

<style lang="scss">
.hideSidebar {
  width: calc(100% - 54px);
}

</style>
