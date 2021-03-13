<template>
  <div id="app">
    <h3>新增單筆：</h3>
        <label for="name">名稱
            <input id="name" type="text" v-model="product.name">
        </label>
        <label for="price">單價
            <input id="price" type="text" v-model="product.price">
        </label>
        <label for="num">數量
            <input id="num" type="text" v-model="product.num">
        </label>
        <input type="button" value="新增" v-on:click="insertList(product)">
        <h3>購物清單：</h3>
        <ul>
            <li v-for="products in display">
                名稱：{{products.name}} 單價：{{products.price}} 數量：{{products.num}}
                <input type="button" value="刪除" v-on:click="deleteList(products)">
            </li>
        </ul>
        <br>
        <span>總價：{{result}}元</span>
  </div>
</template>

<script>
export default {
  name: 'App'
}
</script>

<style>


#app {
  font-family: 'Avenir', Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}
</style>
