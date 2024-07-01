<script setup lang="ts">
import { defineEmits } from 'vue';
import IconPlus from '@/components/icon/IconPlus.vue';

const emits = defineEmits(['file-loaded']);

function add_file() {
    const input = document.createElement('input');
    input.type = 'file';
    input.accept = '.txt';
    input.onchange = (event) => {
        const file = event.target.files[0];
        if (file) {
            const reader = new FileReader();
            reader.onload = (e) => {
                const contents = e.target.result;
                // console.log('File contents:', contents);
                emits('file-loaded', contents);
            };
            reader.readAsText(file);
        }
    };
    input.click();
    // console.log('Add file');
}
</script>

<template>
    <div id="topbar-warpper">
        <button @click="add_file" id="add-file">
            <IconPlus />
        </button>
    </div>
</template>

<style scoped>
#topbar-warpper {
    display: flex;
    justify-content: flex-end;
    padding: 10px;
    background-color: #f5f5f5;
}
</style>
