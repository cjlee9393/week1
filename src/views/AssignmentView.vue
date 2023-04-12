<script>
import card from '../components/card.vue';
export default {
  // component options
  data() {
    return {
      picked: 'Customer',
      pokemon1: {
        stock: 0
      },
      pokemon2: {
        stock: 0
      },
      stockInput: 0
    }
  }, 
  methods: {
    order(pokemon) {
      pokemon.stock--;
    },
    editStock(pokemon, stockInput) {
      pokemon.stock = stockInput;
    }
  },
  components: {
    card
  }
  // declare some reactive state here.
}
</script>

<template>
  <main>
    <div id="auth">
      <div>권한 선택: {{ picked }}</div>

      <input type="radio" id="Customer" value="Customer" v-model="picked" />
      <label for="Customer">Customer</label>

      <input type="radio" id="Admin" value="Admin" v-model="picked" />
      <label for="Admin">Admin</label>
    </div>

    <div id="card-container">
      <card v-for="pokemon in ['pokemon1', 'pokemon2']" :pokemon="pokemon" :picked="picked" />
    </div>
    
    <!-- <div v-if="this.picked=='Customer'" id="card-customer">
      <img src="../assets/pokemon1.png">
      <div v-if="pokemon1.stock">
        <p>재고: {{ pokemon1.stock }}</p>
        <button @click="order(pokemon1)">주문</button>
      </div> 
      <p v-else>재고 없음</p>
    </div>
    <div v-if="this.picked=='Admin'" id="card-admin">
      <img src="../assets/pokemon1.png">
      <p>재고: {{ pokemon1.stock }}</p>
      <div id="edit-stock">
        <p>재고수정</p>
        <input v-model="stockInput">
        <button @click="editStock(pokemon1, stockInput)">입력</button>
      </div>
    </div> -->

  </main>
</template>

<style>
#card-container {
  width: 600px;
  display: flex;
  flex-direction: row;
  justify-content: space-around;
}
</style>