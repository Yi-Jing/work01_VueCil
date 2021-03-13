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
  name: 'app',
  data(){
    return {
      product: [{
            name: '',
            price: 0,
            num: 0
        }],
        display: []
    }
  },
  computed: {
    result (){
        var sum=0;
        this.display.forEach(i => {
            sum+=i.price*i.num;
        });
        return sum
    }
    },
    methods: {
      insertList (products){
          let ins = this
          if(products.name==null || products.price==null || products.num==null){
              alert("請輸入完整資料");
          }
          else if (products.price<0 || products.num<0){
              alert("單價或數量請輸入正整數");
          }
          else if(products.num%1!=0){
              alert("數量請輸入正整數");
          }
          else{
              ins.display.push({name: products.name, price: products.price, num: products.num})
          }
      },
      deleteList (products){
          let del = this
          del.display.splice(del.display.indexOf(products), 1);       
      }
    }
}
</script>

<style></style>
