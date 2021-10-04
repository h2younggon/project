<template>
  <div class="container">
    <base-header />
    <div class="app-body">
      <router-view />
    </div>
  </div>
</template>

<script lang="ts">
import { defineComponent } from 'vue';
import BaseHeader from './components/common/BaseHeader.vue';

export default defineComponent({
  components: { BaseHeader },
  setup() {
    return {};
  },
});
</script>

<style scoped lang="scss">
.container,
.app-body {
  height: 100%;
}
</style>
