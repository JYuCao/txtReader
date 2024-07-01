<script setup lang="ts">
import { defineProps, computed } from 'vue';

const props = defineProps({
    contents: String
});

const contents = computed(() => {
    return props.contents.split('\n');
});
</script>

<template>
    <div id="content-warpper">
        <p v-for="(paragraph, index) in contents" :key="index">
            {{ paragraph }}
        </p>
    </div>
</template>

<style scoped>
#content-warpper {
    background-color: #f5f5f5;
    padding-left: 10rem;
    padding-right: 10rem;
    padding-bottom: 5rem;
}

#content-warpper p {
    font-size: 1.2rem;
    line-height: 2rem;
    text-indent: 2em;
}
</style>
