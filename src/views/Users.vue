<template>
    <div>
        <h2>Список пользователей</h2>
        <div v-if="loading" class="alert alert-warning">
            Loading.........
        </div>
        <div v-else-if="!users.length">
            Нет пользователей
        </div>
        <user-list v-else :users="users"></user-list>
        <button type="button" class="btn btn-primary" @click="loadData">
            UPDATE
        </button>
    </div>

</template> 
<script>
import axios from 'axios';
import UserList from '@/components/UserList.vue';
export default {
  components: {
    'user-list': UserList
  },
  data: () => ({
    users: [],
    loading: true
  }),
  mounted() {
    this.loadData();
  },
  methods: {
    loadData() {
      this.loading = true;
      axios
        .get('http://127.0.0.1:3000/users')
        .then(response => {
          this.loading = false;
          this.users = response.data;
        })
        .catch(error => {
          console.log(error);
        });
    }
  }
};
</script>
