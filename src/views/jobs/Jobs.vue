<template>
    <div>
        <h1>There is a jobs</h1>
        <div v-for="job in jobs" :key="job.id">
            <router-link :to="{name: 'JobDetail', params: {id: job.id}}">
                <h1>{{ job.name }} </h1>
            </router-link>
            <!-- <JobDetail :job="job"/> -->
        </div>
    </div>
</template>

<script>

// import { json } from 'body-parser';
import JobDetail from './JobDetail.vue'

export default {

    components: {
        JobDetail
    },

    data() {
        return {
            jobs: [],
        };
    },

    mounted() {
        fetch("http://localhost:3000/jobs")
        .then(reponse => reponse.json())
        .then(data => this.jobs = data)
        .catch(err => console.log(err.message))
    }
};
</script>

<style></style>
