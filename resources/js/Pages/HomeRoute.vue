<script setup>

import axios from "axios";
import { ref } from "vue";

const response = ref();

const getValue = async () => {
    try {
        response.value = await axios.get("/api/test-me");
    } catch (error) {
        // Do something with the error
        console.log(error);
    }
};

</script>

<template>
    <div>
        <h2>HOME</h2>
        <p>
            <router-link to="/test"> Take me to Test page </router-link>
        </p>
        <p>
            <button class="btn btn-primary" type="button" @click.prevent="getValue()">Trigger Endpoint</button>
            <p v-if="response">{{ response.data }}</p>
        </p>
    </div>
</template>