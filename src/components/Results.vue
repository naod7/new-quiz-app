<script setup>

    import {defineProps} from 'vue'

    const {correctAnswers, questions} = defineProps(['correctAnswers', 'questions'])
</script>


<template>
    <div class="results">
        <p>Your Results...</p>
        <h1>
            {{ correctAnswers }}/{{ questions }}
        </h1>
        <RouterLink to="/">Go Back</RouterLink>
    </div>
</template>


<style scoped>

    .results {
        text-align: center;
        padding: 100px 0;
    }

    p {
        font-size: 25px;
    }

    h1 {
        font-size: 80px;
    }
</style>