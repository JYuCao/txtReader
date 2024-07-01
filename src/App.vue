<script setup lang="ts">
import { ref } from 'vue';

import TopBar from '@/components/TopBar.vue';
import ContentField from '@/components/ContentField.vue';
import SideBar from '@/components/SideBar.vue';

const fileContents = ref<string>('');
const sidebarHeight = ref<string>('0');
var directoryData = ref<any[]>([]);

function handleFileLoaded(contents: string) {
  fileContents.value = contents;
  // console.log('File contents:', contents);
}

function handleToggleSidebar() {
  sidebarHeight.value = sidebarHeight.value === '0' ? '100vh' : '0';
}

function handleDirectory(fileNamesJson: Object) {
  directoryData = fileNamesJson;
  console.log('File names:', directoryData);
}

</script>

<template>
  <nav>
    <TopBar 
      @directory-loaded="handleDirectory" 
      @file-loaded="handleFileLoaded" 
      @toggle-sidebar="handleToggleSidebar" 
    />
  </nav>
  <div>
    <ContentField :contents="fileContents" />
    <SideBar :style="{ height: sidebarHeight }"
            :directoryData="directoryData"
    />
  </div>
</template>

<style scoped></style>
