<template>
    <div>
        {{ fullName }}
    </div>
</template>

<script>
import { toRefs, computed } from 'vue';

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

        const foo = () => console.log()

        expose({
            fullName,
            foo
        })
    }
}
</script>