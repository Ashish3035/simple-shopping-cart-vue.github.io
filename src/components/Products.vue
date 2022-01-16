<template>
  <div class="bg-grey">
    <h3 class="text-4xl font-normal leading-normal mt-0 mb-2 text-black-800">
      Products
    </h3>

    <div
      class="
        grid grid-cols-1
        gap-y-10
        sm:grid-cols-2
        gap-x-6
        lg:grid-cols-3
        xl:grid-cols-4 xl:gap-x-8
      "
    >
      <div v-for="product in products" :key="product.id">
        <div
          class="
            w-full
            aspect-w-1 aspect-h-1
            bg-gray-200
            rounded-lg
            overflow-hidden
            xl:aspect-w-7 xl:aspect-h-8
          "
        >
          <img
            :src="product.imageSrc"
            :alt="product.imageAlt"
            class="
              w-full
              h-full
              object-center object-cover
              group-hover:opacity-75
            "
          />
        </div>
        <h3 class="mt-4 text-sm text-gray-700">
          {{ product.title }}
        </h3>
        <p class="mt-1 text-lg font-medium text-gray-900">
          Price:
          {{ product.price }}
        </p>

        <button
          @click="addToCart(product)"
          class="bg-indigo-500 text-gray-100 mt-2 px-5 ml-9 ..."
        >
          Add
        </button>
      </div>
    </div>
  </div>
</template>

<script>
export default {
  name: "Index",
  props: ["products"],
  //   data() {
  //     return {
  //       id: this.id,
  //       title: this.title,
  //       price: this.price,
  //     };
  //   },
  methods: {
    addToCart(product) {
      // const selectedProduct = this.products[index];

      this.$emit("add-to-cart", product);
    },
  },
};
</script>