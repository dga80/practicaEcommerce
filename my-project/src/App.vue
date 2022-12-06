<script>
import LIST from "./items.json";
export default {
  data () {
    return {
      items: LIST,
    }
  },
  computed:{
    result () {
      return this.item===active
    }
  }
}
</script>

<template>
  
  <article class="flex justify-around">
    <div>
      <ul v-for="item of items">
        <li class="pb-20" v-if="active"></li>
      </ul>
    </div>
    <div>
      <ul v-for="item of items">
        <li class="pb-10"><img :src="item.image" :alt="item.name" class="w-20"></li>
      </ul>
    </div>
    <div>
      <ul v-for="item of items">
        <li class="pb-20">{{item.price}}</li>
      </ul>
    </div>
    <div>
      <ul v-for="item of items">
        <li class="pb-20">
          <input type="number" v-model="item.quantity" class="text-right border-2 border-stone-900"/>
        </li>
      </ul>
    </div>
    <div>
      <ul v-for="item of items">
          <li class="pb-20">{{item.price * item.quantity}}</li>
      </ul>
    </div>
  </article>
  
</template>

<style scoped>
  .articleSize{
    height: 100vh;
    }
</style>
