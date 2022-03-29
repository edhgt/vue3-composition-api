<template>
    <div>
        {{ text }}
        {{ counter }}
    </div>
</template>

<script>
import { ref, reactive } from 'vue';

export default {
    setup() {
        /*
        Para tipos primitivos: string, number, bigint, boolean, undefined, symbol
        */
        const text = ref("Hola Vue");
        const counter = ref(0);

        // leer variable
        text.value

        // asignar
        text.value = "Que hay de nuevo viejo"

        setInterval(() => counter.value++, 500)

        /*
        Para objetos literales
        */
        const obj = reactive({ counter: 0 })
        obj.counter
        obj.counter++

        setInterval(() => obj.counter++, 500)

        return {
            text,
            counter,
            obj
        }
    }
}
</script>