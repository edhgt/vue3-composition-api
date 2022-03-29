<template>
    <div>
        <div>{{ fullName }}</div>
        <div>{{ username }}</div>
        <button ref="btn">Click!</button>
    </div>
</template>

<script>
import { ref, toRefs, computed, watch, inject } from 'vue';

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

        const { refs, firstName, lastName } = toRefs(props)

        const fullName = computed(() => {
            return `${firstName.value} ${lastName.value}`
        });

        const username = inject('username');

        const foo = () => console.log()

        expose({
            fullName
        });
        const btn = ref(null);

        console.log(btn.value)

        watch(btn, (valor) => {
            console.log(valor)
        })

        return ({
            fullName,
            foo,
            username,
            btn
        });
    }
}
</script>