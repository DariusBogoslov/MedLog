<template>
  <div id="view-user">
    <ul class="collection with-header">
      <li class="collection-header"><h4>{{lastname}} {{firstname}}</h4></li>
      <li class="collection-item">Address: {{address}}</li>
      <li class="collection-item">City: {{city}}</li>
      <li class="collection-item">County: {{county}}</li>
      <li class="collection-item">Email: {{email}}</li>
      <li class="collection-item">Telephone: {{telephone}}</li>
      <li class="collection-item">CI: {{CI}}</li>
      <li class="collection-item">CNP: {{CNP}}</li>
      <li class="collection-item">Status: {{status}}</li>
    </ul>
    <router-link to="/" class="btn grey">Back</router-link>
    <button @click="deleteUser" class="btn red">Delete</button>
  </div>
</template>

<script>
import db from './firebaseInit'
export default {
  name: 'view-user',
  data(){
      return {
        id: null,
        user_id: null,
        user_class: null,
        firstname: null,
        lastname: null,
        address: null,
        city: null,
        county: null,
        email: null,
        telephone: null,
        CI: null,
        CNP: null,
        status: null
      }
  },
  beforeRouteEnter (to, from, next){
    db.collection('users').where('user_id', '==', to.params.user_id).get()
    .then(querySnapshot => {
      querySnapshot.forEach(doc => {
        next(vm => {
          vm.user_id = doc.data().user_id
          vm.user_class = doc.data().user_class
          vm.firstname = doc.data().firstname
          vm.lastname = doc.data().lastname
          vm.address = doc.data().address
          vm.city = doc.data().City
          vm.county = doc.data().County
          vm.email = doc.data().email
          vm.telephone = doc.data().telephone
          vm.CI = doc.data().CI
          vm.CNP = doc.data().CNP
          vm.status = doc.data().Status
        })
      })
    })
  },
  watch: {
    '$route': 'fetchData'
  },
  methods: {
    fetchData () {
      db.collection('users').where('user_id', '==', this.$route.params.user_id).get()
      .then(querySnapshot => {
        querySnapshot.forEach(doc => {
          this.user_id = doc.data().user_id
          this.user_class = doc.data().user_class
          this.firstname = doc.data().firstname
          this.lastname = doc.data().lastname
          this.address = doc.data().address
          this.city = doc.data().City
          this.county = doc.data().County
          this.email = doc.data().email
          this.telephone = doc.data().telephone
          this.CI = doc.data().CI
          this.CNP = doc.data().CNP
          this.status = doc.data().Status
        })
      })
    },
    deleteUser () {
      if(confirm('Are you sure?')) {
        db.collection('users').where('user_id', '==', this.$route.params.user_id).get()
       .then(querySnapshot => {
        querySnapshot.forEach(doc => {
          doc.ref.delete()
          this.$router.push('/')
        })
      })
      }
    }
  }
}
</script>
