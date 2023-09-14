<script setup>

    import {defineProps} from 'vue'

    const {questionLength, barPercentage} = defineProps(['questionLength', 'barPercentage'])
</script>


<template>
    <header>
        <h4>Question {{ questionLength }}</h4>
        <div class="bar" >
            <div class="completion" :style="{width: barPercentage}">

            </div>
        </div>
    </header>
</template>

<style scoped>

    header {
        margin-top: 20px;
        margin-bottom: 10px;

        display: flex;
        align-items: center;
        height: 65px;
       /* background: rgb(124, 73, 11);*/
        background: linear-gradient(90deg, #09083d 1.18%, #071130 100%);
        color: white;
        padding: 20px;
        justify-content: space-between;
    }

    header h4 {
        font-size: 30px;
    }

    .bar {
        width: 300px;
        height: 50px;
        border: 3px solid rgb(50, 50, 126)
    }

    .completion {
        height: 100%;
        width: 0%;
        background-color: rgb(50, 50, 126);
    }

</style>
