<template>
  <div id="dashboard">
        <!-- <ul class="collection with-header">
            <li class="collection-header"><h4>Users</h4></li>
            <li v-for="user in users" v-bind:key="user.id" class="collection-item">
                <div class="chip">{{user.user_id}}</div>
                {{user.lastname}} {{user.firstname}} | {{user.email}} | {{user.CNP}}
            </li>
        </ul> -->
        <h3>Users</h3>
        <table class="highlight">
            <thead>
                <tr>
                    <th>ID</th>
                    <th>Last Name</th>
                    <th>First Name</th>
                    <th>Email</th>
                    <th>CNP</th>
                    <th>Status</th>
                    <th></th>
                </tr>
            </thead>
            <tbody>
                <tr v-for="user in users" v-bind:key="user.id">
                    <td>{{user.user_id}}</td>
                    <td>{{user.lastname}}</td>
                    <td>{{user.firstname}}</td>
                    <td>{{user.email}}</td>
                    <td>{{user.CNP}}</td>
                    <td>{{user.status}}</td>
                    <td><router-link class="secondary-content" v-bind:to="{name: 'view-user', params: {user_id: user.user_id}}"><i class="small material-icons blue-text">visibility</i></router-link></td>
                </tr>
            </tbody>
        </table>

    <div class="fixed-action-btn">
        <router-link to="/new" class="btn-floating btn-large green">
            <i class="fa fa-plus"></i>
        </router-link>
    </div>
  </div>
</template>

<script>
import db from './firebaseInit'
export default {
  name: 'dashboard',
  data(){
      return {
          users: []
      }
  }, 
  created() {
      db.collection('users').orderBy('user_id').get().then
      (querySnapshot => {
          querySnapshot.forEach(doc => {
              const data = {
                  'user_id': doc.data().user_id,
                  'user_class': doc.data().user_class,
                  'firstname': doc.data().firstname,
                  'lastname': doc.data().lastname,
                  'address': doc.data().address,
                  'city': doc.data().City,
                  'county': doc.data().County,
                  'email': doc.data().email,
                  'telephone': doc.data().telephone,
                  'CI': doc.data().CI,
                  'CNP': doc.data().CNP,
                  'status': doc.data().Status
              }
              this.users.push(data)
          })
      })
  }
}
</script>
