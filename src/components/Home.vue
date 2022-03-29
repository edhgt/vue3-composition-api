<template>
    <div>
        {{ text }}
        {{ counter }}
    </div>
</template>

<script>
import { ref, reactive, watch } from 'vue';

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

        /*
        Si queremos escuchar el cambio del objeto entero
        */
        watch(obj, (valor, anterior) => {
            console.log(valor, anterior)
        })

        /*
        Si queremos escuchar el cambio en una propiedad
        */
        watch(() => obj.counter, (valor, anterior) => {
            console.log(valor, anterior)
        })

        return {
            text,
            counter,
            obj
        }
    }
}
</script>