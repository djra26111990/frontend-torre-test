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
                 :src="getCompanyImg(post)"
                  alt="Image"
                  class="rounded-0"
                ></b-card-img>
              </b-col>
              <b-col md="6">
                <b-card-body :title="post.objective">
                  <b-card-text>
                    <p>{{ getBaseSalary(post) }}</p>
                  </b-card-text>
                  <b-card-text>
                    <p v-html="post.serpTags.description"></p>
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
      postIDs: [{ id: 'Vrojvpdy' }, { id: 'Yd62lOdp' }, { id: 'VWYzP4wN' }],
      postList: [],
    }
  },
  methods: {
    getCompanyImg(post) {
      return post.serpTags.hiringOrganization.logo
    },
    getBaseSalary(post) {
      let { serpTags } = post
      return `${serpTags.baseSalary.currency}: ${serpTags.baseSalary.value.minValue} - ${serpTags.baseSalary.value.maxValue}`
    },
  },
  mounted: function() {
    this.postIDs.map((elem) => {
      fetch(`http://localhost:3000/api/v1/co/${elem.id}`, {
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
        return post.objective.toLowerCase().includes(this.search.toLowerCase())
      })
    },
  },
}
</script>
