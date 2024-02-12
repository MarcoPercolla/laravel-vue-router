<script>
import { store } from "../store.js"
export default {
    name: "Detail",
    props: ["id"],
    data() {
        return {
            store,
            event: null
        }
    },
    mounted() {
        this.event = this.store.eventList.find(item => item.id == this.id);
        console.log(this.event)
    }
}
</script>

<template>
    <h1>Dettaglio evento {{ event?.id }}</h1>
    <div class="date">{{ event?.date }}</div>

    <h5>{{ event?.name }}</h5>
    <h6>{{ event?.user_id }}</h6>
    <p>Restano <b>{{ event?.available_tickets }}</b> biglietti disponibili.</p>
    <p>{{ event?.user.name }}</p>
    <span v-for="tag in event?.tags">
        {{ tag.name }}</span>
</template>

<style scoped></style> 