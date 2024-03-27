<template>
  <div class="ctr">
    <questions v-if="questionsAnswered < questions.length"/>
    <result v-else />

    <button type="button" class="reset-btn">Reset</button>
  </div>
</template>

<script>
  import Questions from './components/Questions.vue';
  import Result from './components/Result.vue';

  export default {
    name: 'App',
    components: {
      Questions,
      Result
    },
    data() {
      return {
        questionsAnswered: 0,
        questions: [
            {
                q: "O que é Vue.js?", 
                answers: [
                    {
                        text: "Uma biblioteca JavaScript para construir interfaces de usuário",
                        is_correct: false
                    },
                    {
                        text: "Um framework JavaScript progressivo para construir interfaces de usuário",
                        is_correct: true 
                    },
                    {
                        text: "Uma linguagem de programação",
                        is_correct: false 
                    },
                    {
                        text: "Um banco de dados SQL",
                        is_correct: false 
                    }
                ] 
            },
            { 
                q: "Qual diretiva do Vue.js é usada para vincular dados a elementos do DOM?", 
                answers: [
                    {
                        text: "v-bind",
                        is_correct: true
                    },
                    {
                        text: "v-if",
                        is_correct: false 
                    },
                    {
                        text: "v-for",
                        is_correct: false 
                    },
                    {
                        text: "v-on",
                        is_correct: false 
                    }
                ] 
            },
            { 
                q: "Como você cria um componente Vue.js?", 
                answers: [
                    {
                        text: "Usando a função Vue.component",
                        is_correct: true
                    },
                    {
                        text: "Usando a função Vue.create",
                        is_correct: false 
                    },
                    {
                        text: "Usando a função Vue.new",
                        is_correct: false 
                    }
                ] 
            },
        ],
        results: [
            {
                min: 0,
                max: 2,
                title: "Tente novamente!",
                desc: "Estude um pouco mais e você pode ter sucesso!"
            },
            {
                min: 3,
                max: 3,
                title: "Uau, você é um gênio!",
                desc: "Estudar definitivamente valeu a pena para você!"
            }
        ]
      }
    }
  }
</script>

<style>

</style>
