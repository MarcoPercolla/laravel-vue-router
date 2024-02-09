<script>
import { store } from "../store.js" //state management
import AppEventCard from "../components/AppEventCard.vue";
export default {
    name: "HomePage",
    components: {
        AppEventCard
    },
    data() {
        return {
            store
        }
    }
}
</script>

<template>
    <div class="cardContainer">

        <AppEventCard v-for="evento in store.eventList" :evento="evento" />
    </div>
</template>

<style scoped>
.cardContainer {
    width: 80vw;
    display: flex;
    justify-content: start;
    flex-wrap: wrap;
    align-items: center;
    margin: 0 auto;
}
</style> 