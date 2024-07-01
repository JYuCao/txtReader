<script setup lang="ts">
import IconPlus from '@/components/icon/IconPlus.vue';
import IconViewList from '@/components/icon/IconViewList.vue';

const emits = defineEmits(['file-loaded', 'toggle-sidebar', 'directory-loaded']);

function addFiles() {
    const input = document.createElement('input');
    input.type = 'file';
    input.accept = '.txt';
    input.webkitdirectory = true; // Enable selecting directories
    input.onchange = (event) => {
        const files = event.target.files;
        const fileNames = Array.from(files).reduce((acc, file) => {
            if (file.webkitRelativePath) {
            const path = file.webkitRelativePath.split('/');
            const folder = path.slice(0, -1).join('/');
            const name = path[path.length - 1];
            if (!acc[folder]) {
                acc[folder] = [];
            }
            acc[folder].push(name);
            } else {
            if (!acc['']) {
                acc[''] = [];
            }
            acc[''].push(file.name);
            }
            return acc;
        }, {});
        const fileNamesJson = JSON.stringify(fileNames);
        emits('directory-loaded', fileNamesJson);
        // console.log('File names:', fileNamesJson);

        // if (files && files.length > 0) {
        //     Array.from(files).forEach((file) => {
        //         const reader = new FileReader();
        //         reader.onload = (e) => {
        //             const contents = e.target.result;
        //             // console.log('File contents:', contents);
        //             emits('file-loaded', contents);
        //         };
        //         reader.readAsText(file);
        //     });
        // }
    };
    input.click();
    // console.log('Add file');
}

function toggleSidebar() {
    emits('toggle-sidebar');
}

</script>

<template>
    <div id="topbar-warpper">
        <button @click="toggleSidebar" id="show-list">
            <IconViewList class="icon" />
        </button>
        <button @click="addFiles" id="add-file">
            <IconPlus class="icon" />
        </button>
    </div>
</template>

<style scoped>
#topbar-warpper {
    position: fixed;
    top: 0;
    left: 100vw - 640px;
    height: 4rem;
    width: 1280px;
    display: flex;
    justify-content: space-between;
    background-color: #8d7a7a;
}

#topbar-warpper button {
    background-color: #8d7a7a;
    border: none;
    cursor: pointer;
    margin: 0.6rem;
}

.icon {
    width: 2rem;
    height: 2rem;
    fill: #000;
}
</style>
