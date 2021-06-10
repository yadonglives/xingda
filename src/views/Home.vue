<template>
  <div class="about">
    <v-sidebar2 />
    <!-- <v-header /> -->
    <!-- <v-sidebar /> -->
    <div class="content-box" :class="{ 'content-collapse': collapse }">
      <v-tags></v-tags>
      <div class="content">
        <router-view v-slot="{ Component }">
          <transition name="move" mode="out-in">
            <keep-alive :include="tagsList">
              <component :is="Component" />
            </keep-alive>
          </transition>
        </router-view>
        <!-- <el-backtop target=".content"></el-backtop> -->
      </div>
    </div>
  </div>
</template>
<script>
import vHeader from '../components/Header';
import vSidebar from '../components/Sidebar';
import vSidebar2 from '../components/Sidebar2';
import vTags from '../components/Tags.vue';
export default {
  components: {
    vHeader,
    vSidebar,
    vSidebar2,
    vTags
  },
  computed: {
    tagsList() {
      return this.$store.state.tagsList.map(item => item.name);
    },
    collapse() {
      return this.$store.state.collapse;
    }
  }
};
</script>
