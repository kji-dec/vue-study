<template>
  <div>
    <h1>Sales Product({{ cart.length }}) - {{ totalPrice }}원</h1>
    <h3> 구입목록 </h3>
    <cart-list :cart-data="cart" @delete-item="deleteWork"></cart-list>
    <br>
    <product-list :chips-data="chips" like="10" @add-item="addWork"></product-list>
    <hr />
  </div>
</template>

<script>
import ProductList from './components/ProductList.vue'
import CartList from './components/CartList.vue'

export default {
  components: {
    ProductList,
    CartList,
  },
  data() {
    return {
      chips: [{
        img: `mango.jpg`,
        title: `자연그대로 망고칩`,
        desc: `단맛이 그대로 살아있는 망고칩입니다.`,
        price: 2500,
      },
      {
        img: `apple.jpg`,
        title: `천연 오가닉 사과칩`,
        desc: `깨끗한 재료를 엄선하여 자연을 그대로 담았습니다.`,
        price: 2000,
      },
      {
        img: `jujube.jpg`,
        title: `아이깨끗 대추칩`,
        desc: `새콤함이 살아있는 반건조 대추그대로.`,
        price: 3000,
      },
      ],
      cart: [],
    }
  },
  computed: {
    totalPrice() {
      let result = 0
      this.cart.forEach((item) => result += item.price);
      return result;
    }
  },
  methods: {
    addWork(idx) {
      const chip = this.chips[idx];
      this.cart.push(chip);
    },
    deleteWork(idx) {
      this.cart.splice(idx, 1);
    },
  },
}
</script>

<style>
* {
  margin: 0;
  padding: 0
}

li {
  list-style: none;
}

body {
  padding: 30px;
}

.list {
  margin: 20px 0;
  display: flex;
}

.list>li {
  width: 200px;
  border: 1px solid gray;
  padding: 10px;
  margin: 5px;
}

.list>li>* {
  display: block
}

.list>li>img {
  width: 200px;
  margin-bottom: 20px;
}

.list>li>strong {
  font-size: 20px;
  color: #666;
  margin-bottom: 10px
}

.list>li>span {
  margin-bottom: 10px;
}

.list>li>button {
  background-color: beige;
  border-color: beige;
}
</style>
