<template>
  <h3 class="text-4xl font-normal leading-normal text-black-800">Your Cart</h3>
  <div class="container flex justify-center my-20">
    <div class="flex flex-col">
      <div class="w-full">
        <div class="border-b border-gray-200 shadow">
          <table>
            <thead class="bg-gray-50">
              <tr>
                <th class="px-6 py-2 text-xs text-gray-500">Product</th>
                <th class="px-6 py-2 text-xs text-gray-500">Title</th>
                <th class="px-6 py-2 text-xs text-gray-500">Price</th>
                <th class="px-6 py-2 text-xs text-gray-500">Quantity</th>
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
                  <button @click="increase(product)">+</button>
                  {{ product.quantity }}
                  <button @click="decrease(product)">-</button>
                </td>
                <button
                  @click="removeFromCart(index)"
                  class="bg-red-500 text-gray-100 mt-2 px-5 ml-9 ..."
                >
                  X
                </button>
              </tr>
            </tbody>
          </table>
          <div>
            <div>
              <h2 class="px-6 py-2 text-xl text-gray-500">
                TOTAL AMOUNT: {{ totalCart }}
              </h2>
            </div>
          </div>
        </div>
      </div>
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
    increase(product) {
      this.carts.map((p) => {
        if (product.id == p.id && p.quantity > 1) {
          p.quantity += 1;
        }
      });
    },
    decrease(product) {
      this.carts.map((p) => {
        if (product.id == p.id && p.quantity > 1) {
          p.quantity -= 1;
        }
      });
    },
    removeFromCart(index) {
      this.cart.splice(index, 1);
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