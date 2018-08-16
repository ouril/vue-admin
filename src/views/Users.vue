<template>
    <div>
        <h2>Список пользователей</h2>
        <div v-if="!users.length" class="alert alert-warning">
            Loading.........
        </div>
        <user-list v-else v-bind:users="users"></user-list>
    </div>
</template> 
<script>
import axios from 'axios';
export default {
  components: {
    'user-list': UserList
  },
  data: function() {
    [];
  },
  mounted: function() {
      this.loadData()
  },
  methods: {
    loadData: function() {
      var self = this;

      axios
        .get('http://127.0.0.1:3000/users')
        .then(function(response) {
          self.users = response.data;
          console.log('паннные пользователей загруженны');
        })
        .catch(function(error) {
          console.log(error);
        });
    }
  }
};
</script>
