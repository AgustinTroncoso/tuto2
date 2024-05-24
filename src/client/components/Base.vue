<script>
import {useAppStore} from "../stores/index.js";

export default {
    setup() {
// Acceder a la store de la app
const appStore = useAppStore();
return {
appStore
};
},
}
</script>

<template>
    <h3>{{ appStore.dato }}</h3>
</template>