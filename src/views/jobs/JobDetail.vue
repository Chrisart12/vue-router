<template>
    <div v-if="job">
        <h1>{{ job.name }} </h1>
        <p>{{ job.detail }} </p>
        <!-- <p>dddddddddddddddddddd</p> -->
        <!-- <div>{{ job.detail }} </div> -->
    </div>
</template>

<script>
export default {

    props: [
        "id"
    ],

    data() {
        return {
            // id: this.$route.params.id
            job: null
        }
    },

    mounted() {
        fetch(`http://localhost:3000/jobs/${this.id}`)
        .then(reponse => reponse.json())
        .then(data => this.job = data)
        .catch(err => console.log(err.message))
    }

}
</script>

<style>

</style>