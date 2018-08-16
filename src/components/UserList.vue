<template>
            <table class="table table-hover">
              <tr v-for="user in users" v-bind:key="user.id">
                <td>
                  {{ user.firstName }}
                </td>
                <td>
                    {{ user.lastName }}
                </td>
                <td>
                    {{ user.balance }}
                </td>
                <td>
                    {{ user.email }}
                </td>
                <td>
                    {{ user.phone }}
                </td>
                <td>
                    {{ user.registered }}
                </td>
                <td>
                  <button class="btn" type="button" v-on:click="remove(user.id)">
                    x
                  </button>
                </td>
              </tr>
            </table>
</template>
<script>
export default {
  props: {
    // Ждём входными параметрами массив с пользователями
    users: {
      type: Array,
      required: true
    }
  },
  computed: {
    total: function() {
      return this.users.length;
    }
  }
};
</script>
