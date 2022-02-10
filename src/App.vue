<template>
  <Products :products="products" v-on:add-to-cart="addToCart" />
  <Cart :carts="carts" />
</template>

<script>
import Products from "./components/Products.vue";
import Cart from "./components/Cart.vue";
import "./assets/tailwind.css";

export default {
  components: {
    Products,
    Cart,
  },
  data() {
    return {
      carts: [],
      products: [
        {
          id: 1,
          title: "Nike Black Addition",
          price: 15,
          quantity: 1,
          imageSrc: require("./assets/images/nike-black.jpg"),
        },
        {
          id: 2,
          title: "Nike Red Addition",
          price: 25,
          quantity: 1,
          imageSrc: require("./assets/images/nike-red.jpg"),
        },
        {
          id: 3,
          title: "Nike White Addition",
          price: 35,
          quantity: 1,
          imageSrc: require("./assets/images/nike-white.jpg"),
        },
        {
          id: 4,
          title: "Addidas Black Addition",
          price: 50,
          quantity: 1,
          imageSrc: require("./assets/images/Black-Addidas.jpg")
        },
      ],
    };
  },
  methods: {
    addToCart(product) {
      const index = this.carts.findIndex((p) => {
        return p.id === product.id;
      });
      if (index === -1) {
        this.carts.push(product);
      } else {
        this.carts[index].quantity++;
      }

      // console.log(product);
    },
  },
};
</script>

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}
</style>
