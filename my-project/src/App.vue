<script>
import LIST from "./items.json";
export default {
  data () {
    return {
      items: LIST,
    }
  }
}
</script>

<template>
  <div>
    <article v-for="item of items" class="flex">
      <p>{{item.name}}</p>
      <img :src="item.image" :alt="item.name" class="w-40">

    </article>
  </div>
</template>

<style scoped>
</style>
