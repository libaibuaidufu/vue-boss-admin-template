<template>
  <div class="admin-aside">
    <el-scrollbar wrap-class="scrollbar-wrapper">
      <el-menu
        class="el-menu-vertical-demo"
        :default-active="activeMenu"
        @open="handleOpen"
        @close="handleClose"
        :collapse="isCollapse"
        :unique-opened="false"
        :collapse-transition="false"
        text-color="#BFCBD9"
        background-color="#304156"
      >
        <sidebar-item
          v-for="route in routes"
          :key="route.path"
          :item="route"
          :base-path="route.path"
        />
      </el-menu>
    </el-scrollbar>
  </div>
</template>

<script>
import { mapGetters } from "vuex";
import SidebarItem from "./SidebarItem";
export default {
  name: "Sidebar",
  components: {
    SidebarItem,
  },
  data() {
    return {};
  },
  computed: {
    ...mapGetters(["sidebar"]),
    activeMenu() {
      const route = this.$route
      const { meta, path } = route
      // if set path, the sidebar will highlight the path you set
      if (meta.activeMenu) {
        return meta.activeMenu
      }
      return path
    },
    isCollapse() {
      return !this.$store.state.app.sidebar.opened;
    },
    routes() {
      return this.$router.options.routes;
    },
  },

  methods: {
    handleOpen(key, keyPath) {
      console.log(key, keyPath);
    },
    handleClose(key, keyPath) {
      console.log(key, keyPath);
    },
  },
};
</script>

<style>
.el-menu-vertical-demo:not(.el-menu--collapse) {
  width: 200px;
  min-height: 400px;
}
</style>
