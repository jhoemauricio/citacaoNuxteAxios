<template>
  <div class="centralizar">
    <h2 class="cor-texto">Citações</h2>
    <div v-for="citacao in citacoes">
      <!-- Citação -->
      <b>"{{ citacao.quote }}"</b><br />
      <p>{{ citacao.author }}</p>
    </div>
  </div>
</template>


<script>

export default {
  data() {
    return {
      citacoes: [],
    };
  },

  methods: {
    carregarFrases() {
      this.$axios.get("https://dummyjson.com/quotes").then((response) => {
        this.citacoes = response.data.quotes;
      });
    },
  },
  created() {
    this.carregarFrases();
  },
};
</script>



<style scoped>
.centralizar {
  text-align: center;
}
.cor-texto {
  color: red;
}
</style>
