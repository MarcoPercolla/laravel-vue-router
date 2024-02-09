<script>
import { store } from "../store.js" //state management
import register from "../debug.js" //per debuggare il componente da console

export default {
    name: "AppHeader",
    data() {
        return {
            menuItems: [
                {
                    routeName: "home",
                    label: "Homepage"
                },
                {
                    routeName: "about",
                    label: "Chi siamo"
                },

            ]
        }

    },
}
</script>

<template>
    <div v-for="(item, index) in menuItems" :key="index">
        <router-link :to="{ name: item.routeName }">
            {{ item.label }}
        </router-link>
    </div>
</template>

<style scoped lang="scss">
// importo variabili
// @use './styles/partials/variables' as *;

// ...qui eventuale SCSS di AppHeader
</style>