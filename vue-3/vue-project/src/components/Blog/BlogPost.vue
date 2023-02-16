<!-- BlogPost.vue -->
<script setup>
const props = defineProps(['title'])
const emit = defineEmits(['enlarge-text', 'deslarge-text'])

console.log(props.title)
// console.log(emit.enlarge-text)

</script>

<template>
    <div class="blog-post">
        <h4>{{ title }}</h4>
        <button @click="$emit('enlarge-text')">Enlarge Text</button>
        <button @click="$emit('deslarge-text')">Deslarge Text</button>
    </div>
</template>
