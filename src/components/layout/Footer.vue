<template>
    <footer>
        Powered by {{ developer }}
    </footer>
</template>
<script>
import { ref } from 'vue'
export default {
    name:'Footer',
    setup() {
       const developer= ref('Linktrain');
    return {
        developer
    }
    },
}
</script>