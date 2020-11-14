<template>
  <div class="home">
    <NavBar />
    <SearchFilter />
  </div>
</template>

<script>
// @ is an alias to /src
import NavBar from '@/components/NavBar.vue'
import SearchFilter from '@/components/SearchFilter.vue'

export default {
  name: 'Home',
  components: {
    NavBar,
    SearchFilter
  }
}
</script>
