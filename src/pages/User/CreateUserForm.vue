<template>
  <card class="card" title="Crear Usuario">
    <div>
      <form @submit.prevent>
        <div class="row">
          <div class="col-md-6">
            <fg-input type="text" label="First Name" placeholder="First Name" v-model="user.name">
            </fg-input>
          </div>
          <div class="col-md-6">
            <fg-input type="text" label="Last Name" placeholder="Last Name" v-model="user.lastname">
            </fg-input>
          </div>
          <div class="col-md-4">
            <fg-input type="email" label="Email" placeholder="Email" v-model="user.email">
            </fg-input>
          </div>
        </div>

        <div class="row">
          <div class="col-md-6">
            <fg-input type="date" label="BirthDay" placeholder="BirthDay" v-model="user.birthday">
            </fg-input>
          </div>
          <div class="col-md-6">
            <fg-input type="text" label="Phone" placeholder="Number Phone" v-model="user.phone">
            </fg-input>
          </div>
        </div>

        <div class="text-center">
          <p-button type="info" round @click.native.prevent="create">
            Create User
          </p-button>
        </div>
        <div class="clearfix"></div>
      </form>
    </div>
  </card>
</template>
<script>
import axios from 'axios';

export default {
  data() {
    return {
      user: {
        email: "example@domain.com",
        name: "Jhon",
        lastname: "Doe",
        phone: "124-5874-523",
        birthday: "",
      },
    };
  },
  methods: {
    create() {
      axios.post('http://localhost:3000/users', {
        ...this.user
      })
        .then(function (response) {
          console.log(response);
        })
        .catch(function (error) {
          console.log(error);
        });
    },
  },
};
</script>
<style></style>
