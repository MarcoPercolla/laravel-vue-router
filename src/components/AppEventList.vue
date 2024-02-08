<script>
import { store } from "../store.js" //state management

export default {
    name: "AppEventList",
    data() {
        return {
            store
        }
    }
}
</script>

<template>
    <div class="cardContainer">



        <div class="card" v-for="evento in store.eventList">
            <div class="cardCase">
                <div class="date">{{ evento.date }}</div>

                <h5>{{ evento.name }}</h5>
                <h6>{{ evento.user_id.name }}</h6>
                <p>Restano <b>{{ evento.available_tickets }}</b> biglietti disponibili.</p>
            </div>
            <div class="cardFooter">
                <a href="#" class="cardBtn">

                    <span>prenota</span>
                </a>
            </div>

        </div>




    </div>
</template>
<style scoped lang="scss">
.cardContainer {
    width: 80vw;
    display: flex;
    justify-content: start;
    flex-wrap: wrap;
    align-items: center;
    margin: 0 auto;
}

.card {
    width: 23%;
    margin: 1%;
    aspect-ratio: 1 % 1.3;
    background-color: orangered;
    border-radius: 1rem;

    display: flex;
    flex-direction: column;



}

.cardCase {
    padding: 1rem;
    height: 80%;
}

.cardFooter {
    width: 100%;
    height: 20%;
    border-radius: 0 0 1rem 1rem;
    background-color: rgba(0, 0, 0, 0.435);
    padding: 0.5rem;


}

.cardBtn {
    background-color: aqua;
    padding: 0.2rem 0.4rem;
    border-radius: 1rem;
}
</style>