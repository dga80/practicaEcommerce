<template class="template">
  <div>
    <header class="pb-[50px]">
      <img src="./assets/vue.svg" width="32" />
      <div>My Ecommerce Cart</div>
      <div class="w-10 border-2 border-slate-400 rounded-lg text-center">{{ numberOfItems }}</div>
    </header>
      <table>
        <thead class="bg-slate-300 text-slate-500">
          <tr class="p-1">
            <th class="text-left">index</th>
            <th class="text-left">name</th>
            <th class="text-left">photo</th>
            <th class="text-left">price</th>
            <th class="text-center">quantity</th>
            <th class="text-right">total</th>
          </tr>
        </thead>

        <tbody>
          <tr v-for="(item, index) of items" :key="index">
            <td>{{index}}</td>
            <td>{{item.name}}</td>
            <td><img :src="item.image" :alt="item.name" width="70" /></td>
            <td>{{item.price}}€</td>
            <td>
              <input class="text-right border-2 border-slate-200"
                type="number"
                v-model.number="item.quantity"
                placeholder="0"
              />
            </td>
            <td class="text-right">{{ priceLine(item) }}€</td>
          </tr>
        </tbody>

        <tfoot>
          <tr>
            <th colspan="6">Total: {{ total }}€</th>
          </tr>
        </tfoot>
      </table>
      <div class="flex justify-between mt-7">
        <AppFooter/>
        <button type="submit" class="w-40 border-2 border-slate-400 rounded-lg text-center items-end">Confirmar compra</button>
      </div>
  </div>
</template>

<script>
import AppFooter from "./components/AppFooter.vue";

const API_URL =
  "https://raw.githubusercontent.com/ironhack-jc/mid-term-api/main/cart";

export default {
  components: {
    AppFooter,
  },
  data() {
    return {
      items: [],
    };
  },
  computed: {
    numberOfItems() {
      let sum = 0;
      for (const item of this.items) {
        sum += item.quantity;
      }
      return sum;
    },
    total() {
      return this.items.reduce(function (accumulator, item) {
        return accumulator + item.price * item.quantity;
      }, 0);
    },
  },
  methods: {
    async fetchApi() {
      const response = await fetch(API_URL);
      this.items = await response.json();
    },
    priceLine(item) {
      return item.price * item.quantity;
    },
  },
  mounted() {
    this.fetchApi();
  },
};
</script>


<style scoped>
header {
  display: flex;
  justify-content: space-between;
}
table {
  width: 100%;
}
table tfoot tr th {
  text-align: right;

}
</style>
