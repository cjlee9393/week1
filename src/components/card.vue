<script>
export default {
  props: {
    pokemon: String,
    picked: String,
  },
  // component options
  data() {
    return {
      stock: 0,
      stockInput: 0,
      imgSrc: `src/assets/${this.pokemon}.png`,
    }
  }, 
  methods: {
    order() {
      this.stock--;
    },
    editStock(stockInput) {
      this.stock = stockInput;
    }
  }
  // declare some reactive state here.
}
</script>

<template>
  <main>
    <div v-if="this.picked=='Customer'" class="card">
      <img :src="imgSrc">
      <div v-if="stock">
        <p>재고: {{ stock }}</p>
        <button @click="order()">주문</button>
      </div> 
      <p v-else style="color:red">재고 없음</p>
    </div>
    <div v-if="this.picked=='Admin'" class="card">
      <img :src="imgSrc">
      <p>재고: {{ stock }}</p>
      <div id="edit-stock">
        <p>재고수정</p>
        <input v-model="stockInput">
        <button @click="editStock(stockInput)">입력</button>
      </div>
    </div>
  </main>
</template>

<style>
img{
  width: 100%;
  height: 250px;
}

main{
  width: 200px;
}

.card {
  display:flex;
  flex-direction:column;
  justify-content: center;
  align-items: center;
}

#edit-stock {
  display: flex;
  flex-direction: row;
  justify-content: space-around;
}

#edit-stock input {
  width: 50%;
}

</style>