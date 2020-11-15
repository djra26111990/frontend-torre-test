<template>
  <b-container>
    <b-row>
      <b-col cols="12" md="12" class="mt-3">
        <b-form-input
          v-model="search"
          placeholder="Enter keyword filter"
          class="mt-3"
        ></b-form-input>
      </b-col>
      <b-col cols="12" md="12" class="mt-3">
        <b-card-group deck v-for="post in filteredList" :key="post.id">

          <b-card no-body class="overflow-hidden mb-3">
            <b-row no-gutters>
              <b-col md="6">
                <b-card-img
                 :src="getPersonImg(post)"
                  alt="Image"
                  class="rounded-1"
                ></b-card-img>
              </b-col>
              <b-col md="6">
                <b-card-body :title="post.person.name">
                  <b-card-text>
                    <p><strong>{{ post.person.professionalHeadline }}</strong></p>
                  </b-card-text>
                  <b-card-text>
                    <p>{{ post.person.summaryOfBio }}</p>
                  </b-card-text>
                </b-card-body>
              </b-col>
            </b-row>
          </b-card>
        </b-card-group>
      </b-col>
    </b-row>
  </b-container>
</template>

<script>
export default {
  name: 'App',
  data() {
    return {
      search: '',
      postIDs: [
        { id: 'djra26111990' }, 
        { id: 'kc' }, 
        { id: 'felixtorrenegrag' }, 
        { id: 'torrenegra' }, 
        { id: 'emiliojimenez' },
        { id: 'taniazapata'}],
      postList: [],
    }
  },
  methods: {
    getPersonImg(post) {
      return post.person.picture
    }
  },
  mounted: function() {
    this.postIDs.map((elem) => {
      fetch(`http://localhost:3000/api/v1/bio/${elem.id}`, {
        method: 'get',
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
      return this.postList.filter((post) => {
        return post.person.name.toLowerCase().includes(this.search.toLowerCase())
      })
    },
  },
}
</script>

<style scoped>
img.rounded-1.card-img {
    border-radius: 278px;
    float: left;
    position: relative;
    width: 45%;
    left: 25%;
    top: 10%;
}
.card-body {
  padding: 3.25rem!important;
}
</style>
