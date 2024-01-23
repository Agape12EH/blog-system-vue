<template>
  <div class="row">
    <div class="col-12">
      <card :title="title" :subTitle="subTitle">
        <div slot="raw-content" class="table-responsive">
          <paper-table :data="data" :columns="columns">
          </paper-table>
        </div>
      </card>
    </div>
  </div>
</template>
<script>
import { PaperTable } from "@/components";
import axios from 'axios';

const tableColumns = ["id", "title", "subtitle", "publicationAt", "userId"];

export default {
  components: {
    PaperTable,
  },
  created() {
    axios.get('http://localhost:3000/posts')
      .then(res => this.data = res.data)
      .catch(error => console.error(error))
      .finally(() => console.log('finally'));
  },
  data() {
    return {
      title: "Lista de Posts",
      subTitle: "Se Listan los Post publicados en el Blog",
      columns: [...tableColumns],
      data: null,
    };
  },
};
</script>
<style></style>
