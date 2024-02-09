<script>
import { store } from "../store.js" //state management
import AppEventList from "../components/AppEventList.vue";
export default {
    name: "HomePage",
    components: {
        AppEventList
    },
    data() {
        return {
            store
        }
    }
}
</script>

<template>
    <AppEventList />
</template>

<style scoped></style> 