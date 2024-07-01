<template>
    <li>
        <span>{{ item.name }}</span>
        <ul v-if="item.children">
            <DirectoryItem v-for="(child, index) in item.children" :key="index" :item="child" />
        </ul>
    </li>
</template>

<script setup>
defineProps({
    item: Object
});
</script>