<script>
import { store } from "../store.js"
import axios from "axios";
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

        // this.event = this.store.eventList.find(item => item.id == this.id);
        // console.log(this.event)
        this.getEventDetail();
    },
    methods: {
        getEventDetail() {
            let url = this.store.apiUrl + this.store.apiEventEndpoint + this.id;

            axios.get(url).then(result => {
                if (result.status === 200) {
                    if (result.data.success) {
                        this.event = result.data.payload;
                    } else {
                        console.error("error: chiamata senza successo.");
                    }

                } else if (result.status === 301) {
                    console.error("Error: change in data-location.");
                } else if (result.status === 400) {
                    console.error("Error: request undefined");
                } else if (result.status === 404) {
                    console.error("Error: not found");
                } else if (result.status === 500) {
                    console.error("Error: undefined");
                }
            }).catch(errore => {
                console.error(errore);
            });
        }
    }
    // created() {
    //     console.log("funziona");
    // }
}
</script>

<template>
    <div v-if="id">
        <h1>Dettaglio evento {{ event?.id }}</h1>
        <div class="date">{{ event?.date }}</div>

        <h5>{{ event?.name }}</h5>
        <h6>{{ event?.user_id }}</h6>
        <p>Restano <b>{{ event?.available_tickets }}</b> biglietti disponibili.</p>
        <p>{{ event?.user?.name }}</p>
        <span v-for="tag in event?.tags">
            {{ tag.name }}</span>
    </div>
</template>

<style scoped></style> 