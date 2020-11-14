<template>
    <div>
        <b-form-input v-model="search" placeholder="Enter keyword filter"></b-form-input>
        <div class="mt-3">
            <b-card-group v-for="post in filteredList" :key="post.id" deck>
            
            <b-card bg-variant="dark" :header="post.objective" text-variant="white" class="text-center">
                <b-card-text>Lorem ipsum dolor sit amet, consectetur adipiscing elit.</b-card-text>
            </b-card>

            </b-card-group>
        </div> 
    </div>
</template>

<script>

export default {
  name: 'App',
  data() {
    return {
      search: '',
      postIDs: [
          { id: 'Vrojvpdy' },
          { id: 'Yd62lOdp' }, 
          { id: 'VWYzP4wN' }
      ],
      postList : []
    }
  },
  mounted: function() {
      this.postIDs.map(elem => {
          fetch('https://torre.co/api/opportunities/' + elem.id, {
        method: 'get'
     })
        .then((response) => {
           return response.json()
        })
        .then((jsonData) => {
          this.postList.push(jsonData)
        })
      })
    
    },
    computed: {
    filteredList() {
        
      return this.postList.filter(post => {
        return post.objective.toLowerCase().includes(this.search.toLowerCase())
      })
    }
  }
}
</script>