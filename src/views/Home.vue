<template>
  <div class="home">
    <NavBar />
    <SearchFilterOportunities />
  </div>
</template>

<script>
// @ is an alias to /src
import NavBar from '@/components/NavBar.vue'
import SearchFilterOportunities from '@/components/SearchFilterOportunities.vue'

export default {
  name: 'Home',
  components: {
    NavBar,
    SearchFilterOportunities
  }
}
</script>
