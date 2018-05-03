<template>
  <div id="new-user">
      <h3>New User</h3>
      <div class="row">
        <form @submit.prevent="saveUser" class="col s12">
          <div class="row">
            <div class="input-field col s12">
              <input type="text" v-model="user_id" required>
              <label>User ID: </label>
            </div>
          </div>
          <div class="row">
            <div class="input-field col s12">
              <input type="text" v-model="firstname" required>
              <label>First Name: </label>
            </div>
          </div>
          <div class="row">
            <div class="input-field col s12">
              <input type="text" v-model="address" required>
              <label>Address: </label>
            </div>
          </div>
          <div class="row">
            <div class="input-field col s12">
              <input type="text" v-model="City" required>
              <label>City: </label>
            </div>
          </div>
          <div class="row">
            <div class="input-field col s12">
              <input type="text" v-model="County" required>
              <label>County: </label>
            </div>
          </div>
          <div class="row">
            <div class="input-field col s12">
              <input type="text" v-model="email" required>
              <label>Email: </label>
            </div>
          </div>
          <div class="row">
            <div class="input-field col s12">
              <input type="text" v-model="telephone" required>
              <label>Telephone: </label>
            </div>
          </div>
          <div class="row">
            <div class="input-field col s12">
              <input type="text" v-model="CI" required>
              <label>CI: </label>
            </div>
          </div>
          <div class="row">
            <div class="input-field col s12">
              <input type="text" v-model="CNP" required>
              <label>CNP: </label>
            </div>
          </div>
          <!-- <div class="row">
            <div class="input-field col s12">
              <input type="text" v-model="Status" required>
              <select id="statusSelect">
                <option value="" disabled selected>Please choose an option</option>
                <option value="In hospital">In hospital</option>
                <option value="Not in hospital">Not in hospital</option>
                <label>Status: </label>
              </select>
            </div>
          </div> -->
          <div class="input-field col s12">
    <select>
      <option value="" disabled selected>Choose your option</option>
      <option value="1">Option 1</option>
      <option value="2">Option 2</option>
      <option value="3">Option 3</option>
    </select>
    <label>Materialize Select</label>
  </div>
          <div class="row">
            <div class="input-field col s12">
              <input type="text" v-model="user_class" required>
              <label>User class: </label>
            </div>
          </div>         
        </form>
      </div>
  </div>
</template>

<script>
export default {
  name: 'new-user',
  data(){
      return {
      }
  }
  // mounted(){
  //   var self = this;
  //   $('#statusSelect').material_select();
  //   $('#statusSelect').on('change', function() {
  //     self.$emit("change", this.value)
  //   });
  //   self.$on("change", function(data) {
  //     this.selected = data
  //   });
  // }
}

  $(document).ready(function() {
    $('select').material_select();
  });
</script>
