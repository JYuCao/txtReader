<script setup lang="ts">
import { ref } from 'vue';

import TopBar from '@/components/TopBar.vue';
import ContentField from '@/components/ContentField.vue';
import SideBar from '@/components/SideBar.vue';

const fileContents = ref<string>('');
const sidebarHeight = ref<string>('0');

function handleFileLoaded(contents: string) {
  fileContents.value = contents;
  // console.log('File contents:', contents);
}

function handleToggleSidebar() {
  sidebarHeight.value = sidebarHeight.value === '0' ? '100vh' : '0';
}

</script>

<template>
  <nav>
    <TopBar @file-loaded="handleFileLoaded" @toggle-sidebar="handleToggleSidebar" />
  </nav>
  <div>
    <ContentField :contents="fileContents" />
    <SideBar :style="{ height: sidebarHeight }" />
  </div>
</template>

<style scoped></style>
