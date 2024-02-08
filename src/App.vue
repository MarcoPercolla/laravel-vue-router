<script>
import AppEventList from "./components/AppEventList.vue"

import axios from 'axios'; //importo Axios
import { store } from "./store.js" //state management

export default {
	components: {
		AppEventList
	},
	data() {
		return {
			store
		}
	},
	mounted() {
		this.getEventList();
	},
	methods: {
		getEventList() {

			let url = this.store.apiUrl + this.store.apiEventEndpoint;

			axios.get(url).then(risultato => {
				if (risultato.status === 200 && risultato.data.success) {
					console.log(risultato.data.content);
					this.store.eventList = risultato.data.content;
				} else {

					console.error("la tua chiamata non è andata a buon fine");
				}
			}).catch(errore => {
				console.error(errore);
			});
		}
	}
}
</script>

<template>
	<main>
		<h1>Prenota qui i tuoi biglietti</h1>
		<AppEventList />
	</main>
</template>

<style lang="scss">
// importo il foglio di stile generale dell'applicazione, non-scoped
@use './styles/general.scss';
</style>

<style scoped lang="scss">
// importo variabili
// @use './styles/partials/variables' as *;

// ...qui eventuale SCSS di App.vue
main {
	padding: 1rem;
}
</style>