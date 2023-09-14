<script setup>
  import {ref, watch} from "vue"
  import Card from '@/components/Card.vue'
  import quiz from '@/data/quizes.json'
  const Quizes = ref(quiz)
  const searchSubject = ref("")

  watch(searchSubject, ()=>{
    Quizes.value = quiz.filter((q)=>{
      return q.name.toLowerCase().includes(searchSubject.value.toLowerCase())
    })
  })
</script>

<template>
    <div>
      <header>
        <h1>Quizes</h1>
        <input v-model="searchSubject" type="text" placeholder="Search....">
      </header>
      <div class="options-container">
        <Card
        v-for="Quiz in Quizes"
        :key="Quiz.id"
        :Quiz="Quiz"
        class="card"
        />
      </div>
    </div>

</template>


<style scoped>
  .container {
    max-width: 1000px;
    margin: 0 auto
  }

    header {
      margin-bottom: 10px;
      margin-top: 30px;
      display: flex;
      align-items: center;
      height: 65px;
      background: linear-gradient(90deg, #09083d 1.18%, #071130 100%);
      color: white;
      padding: 20px;
    }

    header h1 {
      font-weight: bold;
      margin-right: 30px;
    }

    header input {
      border: none;
      background-color: rgba(128,128,128,0.1);
      padding: 10px;
      border-radius: 5px;
      color: white;
    }

  .options-container {
      display: flex;
      flex-wrap: wrap;
      margin-top: 40px;
    }


</style>
