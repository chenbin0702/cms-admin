<template>
  <div class="footer flx-center">
    <a href="https://github.com/chenbin0702/cms-admin" target="_blank">
      CMS-Admin v{{ version }} | Copyright © 2022-{{ new Date().getFullYear() }} CMS-Admin Team
    </a>
  </div>
</template>
<script setup lang="ts">
const version: string = __APP_VERSION__;
</script>
<style scoped lang="scss">
@use './index';
</style>
