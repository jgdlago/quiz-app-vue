<template>
  <div class="ctr">

    <transition name="fade" mode="out-in">
      <questions
        v-if="questionsAnswered < questions.length"
        :questions="questions"
        :questionsAnswered="questionsAnswered"
        @question-answered="questionAnswered"
      />
  
      <result v-else :results="results" :totalCorrect="totalCorrect"/>
    </transition>

    <button
      type="button"
      class="reset-btn"
      @click.prevent="reset"
      v-if="questionAnswered === questions.length"
    >
      Reset
    </button>

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
        totalCorrect: 0,
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
          {
            q: "Qual diretiva do Vue.js é usada para renderizar uma lista de itens com base em um array?", 
            answers: [
              {
                text: "v-for",
                is_correct: true
              },
              {
                text: "v-if",
                is_correct: false 
              },
              {
                text: "v-show",
                is_correct: false 
              },
              {
                text: "v-bind",
                is_correct: false 
              }
            ] 
          },
          { 
            q: "Qual diretiva do Vue.js é usada para ouvir eventos DOM?", 
            answers: [
              {
                text: "v-on",
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
                text: "v-bind",
                is_correct: false 
              }
            ] 
          },
          { 
            q: "Qual é a diferença entre v-if e v-show?", 
            answers: [
              {
                text: "v-if remove e recria elementos, enquanto v-show apenas alterna a visibilidade CSS",
                is_correct: true
              },
              {
                text: "v-if e v-show fazem exatamente a mesma coisa",
                is_correct: false 
              },
              {
                text: "v-if é usado para loops, enquanto v-show é usado para condicionais",
                is_correct: false 
              },
              {
                text: "v-if suporta else e else-if, enquanto v-show não",
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
        ],
      };
    },
    methods: {
      questionAnswered(is_correct) {
        if (is_correct) {
          this.totalCorrect++;
        }
        
        this.questionsAnswered++;
      },
      reset() {
        this.questionAnswered = 0;
        this.totalCorrect = 0;
      },
    },
  };
</script>

<style>

</style>
