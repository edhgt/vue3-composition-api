<template>
    <div>
        {{ fullName }}
    </div>
</template>

<script>
import { ref, computed } from 'vue';

export default {
    setup() {
        const firstName = ref('Danilo');
        const lastName = ref('H');

        const fullName = computed(() => {
            return `${firstName.value} ${lastName.value}`
        });

        return {
            fullName
        }
    }
}
</script>