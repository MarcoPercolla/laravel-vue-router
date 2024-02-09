<script>
export default {
    name: "Detail",
    props: ["id"]
}
</script>

<template>
    <h1>Dettaglio evento {{ this.$route.params.id }}</h1>
</template>

<style scoped></style> 