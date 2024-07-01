<script setup lang="ts">
import { computed } from 'vue';

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
    padding: 5rem 10rem;
    height: 90vh;
    z-index: 1;
}

#content-warpper p {
    font-size: 1.2rem;
    line-height: 2rem;
    text-indent: 2em;
}
</style>
