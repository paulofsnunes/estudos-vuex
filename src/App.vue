<template>
  <div id="app">
    <ul>
      <li v-for="livro in $store.state.livros" :key="livro.nome">
        <p>{{livro.nome}}</p>
      </li>
    </ul>
    <h2>Livros Lidos</h2>
    <ul>
      <li v-for="livro in livrosLidos(false)" :key="livro.nome">
        <p>{{livro.nome}}</p>
      </li>
    </ul>
    {{$store.state.acao.acao}}
    <aluno-view/>
    <curso-view/>
  </div>
</template>

<script>

import AlunoView from '@/components/AlunoView.vue'
import CursoView from '@/components/CursoView.vue'
import { mapGetters } from 'vuex'

export default {
  name: 'App',
  components: {
    AlunoView,
    CursoView
  },
  computed: {
    ...mapGetters(["livrosLidos"])
  },
  created() {
    this.$store.dispatch("acao/puxarAcao")
  }
}
</script>

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  color: #2c3e50;
  margin-top: 60px;
}
</style>


<!-- 
  Crie 3 componentes: Aluno, Curso e Aulas
  Aluno e Curso devem estar em App.vue

  Aulas deve ser um componente filho de Curso

  Aulas terá uma lista:
  {
    nome: "HTML e CSS",
    duracao: 15
  },
  {
    nome: "JavaScript",
    duracao: 30
  },
  {
    nome: "UX Design",
    duracao: 20
  }

  Crie um botão para cada aula, onde será possível
  clicar em completar. As aulas completas deverão
  ser colocadas em uma Array dentro de Store.

  Utilize mutações para modificar a Array.

  A Array de aulas completas deverá ser mostrada no
  componente Aluno
-->


