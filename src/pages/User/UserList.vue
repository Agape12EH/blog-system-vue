<template>
  <div class="row">
    <div class="col-12">
      <card :title="title" :subTitle="subTitle" :actions="actions">
        <div slot="raw-content" class="table-responsive">
          <paper-table :data="data" :columns="columns" :actions="actions">
          </paper-table>
        </div>
      </card>
    </div>
  </div>
</template>
<script>
import { PaperTable } from "@/components";
import axios from 'axios';

const tableColumns = ["id", "name", "lastname", "email"];

export default {
  components: {
    PaperTable,
  },
  created() {
    axios.get('http://localhost:3000/users')
      .then(res => this.data = res.data)
      .catch(error => console.error(error))
  },
  data() {

    return {
      title: "Tabla de Usuarios",
      subTitle: "Se listan los Usuarios registrados en el Blog",
      columns: [...tableColumns],
      data: null,
      actions: {
        create: {
          canSee: true,
          button: "Crear Usuario",
          path: "createuser",
          icon: "ti-plus",
        },
        view: {
          canSee: true,
          button: "",
          path: "createuser",
          icon: "ti-eye",
        },
        edit: {
          canSee: true,
          button: "",
          path: "createuser",
          icon: "ti-pencil-alt",
        },
        delete: {
          canSee: true,
          button: "",
          path: "createuser",
          icon: "ti-trash",
        },
      }
    };
  },

};
</script>
<style></style>
