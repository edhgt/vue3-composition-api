<template>
    <div>
        <div>{{ fullName }}</div>
        <div>{{ username }}</div>
    </div>
</template>

<script>
import { toRefs, computed, inject } from 'vue';

export default {
    props: {
        firstName: {
            required: true,
            type: String
        },
        lastName: {
            required: true,
            type: String
        }
    },
    setup(props, { expose }) {

        const { firstName, lastName } = toRefs(props)

        const fullName = computed(() => {
            return `${firstName.value} ${lastName.value}`
        });

        const username = inject('username');

        const foo = () => console.log()

        expose({
            fullName,
            foo,
            username
        })
    }
}
</script>