<script setup lang="ts">
import { ref } from 'vue';
import TopBar from '@/components/TopBar.vue';
import ContentField from '@/components/ContentField.vue';

const fileContents = ref<string>('');

function handleFileLoaded(contents: string) {
  fileContents.value = contents;
  // console.log('File contents:', contents);
}

</script>

<template>
  <nav>
    <TopBar @file-loaded="handleFileLoaded" />
  </nav>
  <div>
    <ContentField :contents="fileContents" />
  </div>
</template>

<style scoped>
</style>
