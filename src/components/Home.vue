<template>
    <div>
        <div>{{ fullName }}</div>
        <div>{{ username }}</div>
        <button ref="btn">Click!</button>
    </div>
</template>

<script setup>
import { defineProps, defineExpose, ref, toRefs, computed, watch, inject } from 'vue';

const props = defineProps({
    firstName: {
        required: true,
        type: String
    },
    lastName: {
        required: true,
        type: String
    }
})

const { refs, firstName, lastName } = toRefs(props)

const fullName = computed(() => {
    return `${firstName.value} ${lastName.value}`
});

const username = inject('username');

const foo = () => console.log()

defineExpose({
    fullName
});
const btn = ref(null);

console.log(btn.value)

watch(btn, (valor) => {
    console.log(valor)
})
</script>