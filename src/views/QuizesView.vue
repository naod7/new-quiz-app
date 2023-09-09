<script setup>
    import {ref, computed} from 'vue'
    import {useRoute} from 'vue-router'
    import quiz from '@/data/quizes.json'
    import Header from  '@/components/Header.vue'
    import Questions from  '@/components/Questions.vue'
    import Results from '@/components/Results.vue'
    //const Quiz = ref(quiz)



    const route = useRoute()

    const quizId = parseInt(route.params.id)
    const currentQuestionIndex = ref(0)
    const correctAnswers = ref(0)
    const showResult = ref(false)
   // console.log(quiz.questions.text)

    const quizQuestions = quiz.find((q)=>{
        return q.id === quizId
    })

    //const questionLength = ref(`${currentQuestionIndex.value} / ${quiz.questions.length}`)
    const questionLength = computed(()=>{
        return `${currentQuestionIndex.value}/${quizQuestions.questions.length}`

    })

    const barPercentage = computed(()=>{
        return `${currentQuestionIndex.value / quizQuestions.questions.length * 100}%`
    })

    function onSelectedOptions(isCorrect){
        if(isCorrect){
            correctAnswers.value++
        }

        if(quizQuestions.questions.length - 1 === currentQuestionIndex.value){
            showResult.value = true
        }

        currentQuestionIndex.value++
    }


</script>

<template>

    <div>

        <Header
            :questionLength="questionLength"
            :barPercentage="barPercentage"
        />
        <div>
            <Questions
                v-if="!showResult"
                :questions="quizQuestions.questions[currentQuestionIndex]"
                @selectOptions="onSelectedOptions"
            />
            <Results
                v-else
                :correctAnswers="correctAnswers"
                :questions="quizQuestions.questions.length"
            />

        </div>
    </div>
</template>