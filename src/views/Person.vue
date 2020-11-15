<template>
  <div class="person">
    <NavBar />
    <SearchFilterPeople />
  </div>
</template>

<script>
// @ is an alias to /src
import NavBar from '@/components/NavBar.vue'
import SearchFilterPeople from '@/components/SearchFilterPeople.vue'

export default {
  name: 'Person',
  components: {
    NavBar,
    SearchFilterPeople
  }
}
</script>
