<script setup>
import * as Icons from '@/components/icons';
</script>

<template>
  <div class="home">
    <div>
            <!-- Home Icons with different stylings -->
            <div class="icons__container" id="home__icons">
              <Icons.HomeIcon />
              <Icons.HomeIcon width="30" height="30" fill="#333333" />
              <Icons.HomeIcon width="40" height="40" fill="#262626" />
              <Icons.HomeIcon width="60" height="60" fill="#000000" />
            </div>
      
            <!-- Home Icons with different stylings -->
            <div class="icons__container" id="settings__icons">
              <Icons.SettingsIcon />
              <Icons.SettingsIcon width="30" height="30" fill="#333333" />
              <Icons.SettingsIcon width="40" height="40" fill="#262626" />
              <Icons.SettingsIcon width="60" height="60" fill="#000000" />
            </div>
    </div>
  </div>
</template>

<style scoped>

.home {
  display: flex;
  justify-content: center;
  align-items: center;
  height: 100vh;
}

.icons__container {
  display: flex;
  align-items: center;
  justify-content: space-between;
  gap: 50px;
  margin-top: 20px;
}

</style>



