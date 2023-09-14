<script setup>
    import {defineProps, defineEmits} from 'vue'

    const {questions} = defineProps(['questions'])
    const emit = defineEmits(['selectOptions'])

    function emitOptions(isCorrect){
       return emit('selectOptions', isCorrect)
    }
</script>

<template>
    <div class="question-container">
         <h1 class="question">
            {{ questions.text }}
         </h1>
     </div>
     <div class="options-container">
         <div  class="option" v-for="option in questions.options" :key="option.id">
             <p class="option-label" @click="emitOptions(option.isCorrect)">{{ option.label }}</p>
             <div class="option-value">
                 <p>{{ option.text }}</p>
             </div>
         </div>
     </div>
 </template>


<style scoped>

    .question-container {
        margin-top: 20px;
    }

    .question {
        font-size: 40px;
        margin-bottom: 20px;
    }

    .option {
        display: flex;
        margin-bottom: 20px;
        cursor: pointer;
    }

    .option-label {
        background-color:  rgb(163, 163, 221);
        width: 50px;
        height: 50px;
        font-size: 30px;
        display: flex;
        align-items: center;
        justify-content: center;
    }

    .option-value {
        background-color: rgb(244,239,239);
        width: 100%;
        font-size: 30px;
        padding: 0 20px;

    }

</style>
