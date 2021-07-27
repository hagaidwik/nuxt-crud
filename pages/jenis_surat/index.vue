<template>
  <b-container fluid="md" class="mt-5 mb-5">
    <b-row>
      <b-col md="12">
        <b-card class="shadow-md border-0 rounded-lg">
          <h5>Jenis Surat</h5>
          <hr />
          <b-button
            :to="{ name: 'jenis_surat-create' }"
            variant="primary"
            class="mb-3"
            >TAMBAH</b-button
          >
          <b-table
            striped
            bordered
            hover
            :items="jenis_surat"
            :fields="fields"
            show-empty
          >
            <template v-slot:cell(actions)="row">
              <b-button
                :to="{ name: 'jenis_surat-edit-id', params: { id: row.item.id } }"
                variant="warning"
                size="sm"
                >EDIT</b-button
              >
              <b-button
              variant="danger"
              size="sm"
              @click="deletejenis_surat(row)"
                >DELETE</b-button
              >
            </template>
          </b-table>
        </b-card>
      </b-col>
    </b-row>
  </b-container>
</template>

<script>
export default {
  data () {
    return {
      fields: ['jenis_surat', 'actions'],
      jenis_surat: []
    }
  },

  mounted () {
    console.log('asik')
    this.$axios
      .get('/api/jenis_surat')
      .then((response) => {
        this.jenis_surat = response.data.data
      })
      .catch((error) => {
          console.log (error.response.data)
      });
  },

  methods: {
    async deletejenis_surat (row) {
      await this.$axios.delete(`/api/jenis_surat/${row.item.id}`).then(() => {
        this.jenis_surat.splice(row.index, 1)
      });
    }
  }
};
</script>

<style></style>
