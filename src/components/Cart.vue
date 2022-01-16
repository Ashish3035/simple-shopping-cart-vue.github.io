<template>
  <table border="2px solid black">
    <thead>
      <tr>
        <th>Product</th>
        <th>Title</th>
        <th>Price</th>
        <th>Quantity</th>
      </tr>
    </thead>
    <tbody>
      <tr v-for="(product, index) in carts" :key="index">
        <th>
          <img :src="product.imageSrc" style="width: 4rem" />
        </th>
        <td>{{ product.title }}</td>
        <td>{{ product.price }}</td>
        <td>
          <button>+</button>
          {{ product.quantity }}
          <button @click="decrease(product)">-</button>
        </td>
        <button
          @click="removeFromCart(index)"
          class="bg-indigo-500 text-gray-100 mt-2 px-5 ml-9 ..."
        >
          X
        </button>
      </tr>
      <!-- <tr>
        <td></td>
        <td></td>
        <td></td>
      </tr> -->
    </tbody>
  </table>
  <div>
    <div>
      <h4>TOTAL AMOUNT: {{ totalCart }}</h4>
    </div>
  </div>
</template>

<script>
export default {
  name: "Cart",
  props: ["carts"],
  data() {
    return {
      cart: this.carts,
    };
  },
  methods: {
    decrease(product) {
      this.carts.map((p) => {
        if (product.id == p.id && p.quantity > 1) {
          p.quantity -= 1;
        }
      });
    },
    removeFromCart(index) {
      this.cart.splice(index, 1)
    },
  },
  computed: {
    totalCart() {
      return this.carts.reduce((total, product) => {
        return (total += product.price * product.quantity);
      }, 0);
    },
  },
};
</script>