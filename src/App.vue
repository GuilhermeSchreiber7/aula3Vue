<script setup>
//Variáveis Reativas
 import { ref } from 'vue';
 // import { reactive } from 'vue';
 //-//

 //propriedades computadas
 //dá pra colocar mais funções em um import, aqui por exemplo tem a reativa e computada
 import { reactive, computed } from 'vue';
 //-//

 //Variáveis Reativas ex.
const contador = ref(0);

function incrementar() {
  contador.value++;
}

const frutas = ref(['maçã', 'banana']); // array de strings

const pessoa = reactive({
    nome: 'João',
    idade: 30,
    ativo: true,
  });

  function aniversario(){
    pessoa.idade++;
  }
//-//

 //propriedades computadas ex.
 const professor = reactive({
    nome: 'Eduardo da Silva',
    disciplinas: [
      'Desenvolvimento Web II',
      'Desenvolvimento de Aplicativos para Dispositivos Móveis',
    ],
  });
  const possuiDisciplinas = computed(() => {
    return professor.disciplinas.length > 0;
  });
</script>

<template>
  <!-- reativas -->
<h1>variáveis reativas</h1>
<br>
<button @click="incrementar">{{ contador }} </button>

<p>{{ frutas }}</p>

<div>
  <p>
    {{ pessoa.nome }} tem {{ pessoa.idade }} anos.
  </p>
  <button @click="aniversario">Fazer aniversário</button>
</div>
<br>
<!-- computada -->
<h1>propriedades computadas</h1>
<br>
<div>
    <h1>Professor</h1>
    <p>Nome: {{ professor.nome }}</p>
    <p v-if="!possuiDisciplinas">O professor não possui disciplinas.</p>
    <div v-else>
      <p>O professor possui disciplinas.</p>
      <ul>
        <li v-for="disciplina in professor.disciplinas" :key="disciplina">
          {{ disciplina }}
        </li>
      </ul>
    </div>
  </div>
</template>


<style scoped>

</style>
