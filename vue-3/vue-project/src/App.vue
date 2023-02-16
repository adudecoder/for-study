<script setup>
import { ref, computed } from 'vue';
const searchValue = ref('')

const products = ref([
  { name: 'Pão Francês', category: 'Pão' },
  { name: 'Molho de Tomate', category: 'Molho' },
  { name: 'Carne moida', category: 'Carnes' },
  { name: 'Tomate', category: 'Legume' }
])

const productsList = computed(() => {
  if (searchValue.value.trim().length > 0) {
    return products.value.filter((product) => product.name.toLowerCase().includes(searchValue.value.trim().toLowerCase()))
  }
  return products.value
})

</script>

<template>
  
  <div id="app">

    <input 
      type="text"
      placeholder="Procurar"
      class="search-input text-black"
      v-model="searchValue"
    />

    <div class="products-container" v-if="productsList.length">
      <div v-for="(product, index) in productsList" :key="index">
        <strong>{{ index + 1 }}</strong> - {{ product.name }}
      </div>
    </div>

    <div v-else>
      Nenhum Ingrediente Encontrado para Pesquisa: {{ searchValue }}
    </div>

  </div>

</template>


<style scoped>
.search-input {
  width: 200px;
  height: 30px;
  border-radius: 2px;
  padding: 5px;
}

.products-container {
  margin-top: 15px;
}
</style>