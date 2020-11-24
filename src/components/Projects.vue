<template>
  <div class="container">
      <div class="table-scroll">
        <table class="table table-stripped">
          <thead class="bg-dark text-white">
            <tr>
              <th class="fixed-col bg-dark">Project name</th>
              <th>Developer</th>
              <th>Main contractor</th>
              <th>Area</th>
              <th>State</th>
              <th>
                <span class="dropdown-text">Status</span>
                <span class="dropdown-icon"></span>
              </th>
              <th>Sector</th>
            </tr>
          </thead>
          <tbody>
            <tr v-for="info in projectInfo" :key="info.id">
              <th class="fixed-col">
                <button class="btn btn-transparent">{{info.project_name}}</button>
              </th>
              <td>{{info.developer}}</td>
              <td>{{info.main_contractor}}</td>
              <td class="no-blur">
                <div class="relative-cell">
                  <span class="has-blur">{{info.lga}}</span>
                  <a href="#" class="view-link"> View project</a>
                </div>
              </td>
              <td>{{info.state}}</td>
              <td class="fixed-w">
                <span class="highlighted">{{info.status}}</span>
              </td>
              <td>{{info.sector}}</td>
            </tr>
          </tbody>
        </table>
      </div>
  </div>
</template>

<script>
import axios from 'axios'

export default {
  name: 'Projects', 

  data () {
    return {
      projectInfo: null
    }
  },
  mounted() {
    this.fetchProjects();   
  }, 
  methods: {
    fetchProjects() {
      axios.get('https://244b8df3-7491-4cfd-a48b-267f19446372.mock.pstmn.io/')
        .then(res => {
          // this.agents = res.data
          this.projectInfo = res.data.data
        })
        .catch(error => this.userInfo = error.data);  
    }
  }
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>

</style>
