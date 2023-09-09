<script setup>

    import {defineProps} from 'vue'
    import {useRouter} from 'vue-router'
    const {Quiz} = defineProps(['Quiz'])

    const router = useRouter()

    function renderQuizes(){
        router.push(`quizes/${Quiz.id}`)
    }
</script>


<template>
    <div>
        <img :src="Quiz.img" @click="renderQuizes">
        <div class="card-text">
            <h2>{{ Quiz.name }}</h2>
            <p>{{ Quiz.questions.length }} questions</p>
        </div>
    </div>
</template>


<style scoped>
.card {
    width: 310px;
    overflow: hidden;
    border-radius: 2%;
    box-shadow: 1px 1px 10px rgba(0,0,0,0.1);
    margin-bottom: 35px;
    margin-right: 20px;
    cursor: pointer;
  }

  .card img {
    width: 100%;
    height: 190px;
    margin: 0
  }

  .card .card-text {
    padding: 0 5px
  }

  .card .card-text h2 {
    font-weight: bold;
  }

</style>