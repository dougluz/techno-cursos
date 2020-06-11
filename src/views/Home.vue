<template>
  <div>
    <div class="centralizado" v-if="loading">
      <PageLoading />
    </div>
    <transition>
      <div class="conteudo" v-if="api">
        <div>
          <h1>Sobre a {{api.titulo}}</h1>
          <p>{{ api.descricao }}</p>
          <router-link tag="button" class="btn-cursos" to="/cursos">Cursos</router-link>
          <div>
            <h2>Avaliações</h2>
            <ul>
              <li v-for="avaliacao in api.avaliacoes" :key="avaliacao.nome">
                <p><b>{{avaliacao.nome}}</b></p>
                <p>{{avaliacao.descricao}}</p>
              </li>
            </ul>
          </div>
        </div>
        <img src="../assets/aprender.png" alt="">
      </div>
    </transition>
  </div>
</template>

<script>
import fetchData from '@/mixins/fetchData.js'

export default {
  name: 'Home',
  mixins: [fetchData],
  created() {
    this.fetchData('/home')
  }
};
</script>

<style scoped>
  .btn-cursos {
    border: none;
    background: #4b8;
    border: 4px;
    color: white;
    cursor: pointer;
    padding: 15px 20px;
    font-size: 1rem;
    margin-top: 10px;
    margin-bottom: 40px;
    box-shadow: 0 4px 2px rgba(0, 0, 0, 0.1);
    font-family: "Avenir", Arial, Helvetica, sans-serif;
  }
</style>
