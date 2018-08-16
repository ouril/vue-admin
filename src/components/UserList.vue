<template id="users-component">
            <table>
              <tr v-for="user in users" v-bind:key="user.id">
                <td>
                  {{ user.firstName }}
                </td>
                <td>
                  {{ user.lastName }}
                </td>
                <td>
                  <button type="button" v-on:click="remove(user.id)">
                    X
                  </button>
                </td>
              </tr>
            </table>
    </template>