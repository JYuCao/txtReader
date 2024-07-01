<script setup lang="ts">
import DirectoryItem from '@/components/DirectoryItem.vue';

const props = defineProps({
    directoryData: Object
});
</script>

<template>
    <div id="sidebar-warpper">
        <ul>
            <DirectoryItem v-for="(item, index) in directoryData" :key="index" :item="item" />
        </ul>
    </div>
</template>

<style scoped>
#sidebar-warpper {
    background-color: #b5a8a8;
    width: 20rem;
    height: 100vh;
    position: fixed;
    top: 4rem;
    left: 100vw - 640px;
    z-index: 2;
    transition: height 0.5s;
}

</style>
