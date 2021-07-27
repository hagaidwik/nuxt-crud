<template>
  <b-container fluid="md" class="mt-5 mb-5">
    <b-row>
      <b-col md="12">
        <b-card class="shadow-md border-0 rounded-lg">
          <h5>EDIT POST</h5>
          <hr>
          <b-form @submit="update">
            <b-form-group label="jenis surat">
              <b-form-input type="text" v-model="jenis_surat.jenis_surat" :class="{ 'is-invalid': validation.title }"
                placeholder="Masukkan jenis surat">
              </b-form-input>
              <div v-if="validation.jenis_surat" class="mt-2">
                 <b-alert show variant="danger">{{ validation.jenis_surat[1] }}</b-alert>
              </div>
            </b-form-group>





            <b-button type="submit" variant="primary">UPDATE</b-button>
          </b-form>
        </b-card>
      </b-col>
    </b-row>
  </b-container>
</template>

<script>
  export default {
    data() {
      return {
        desa: {
          jenis_surat: '',
        },
        validation: []
      }
    },
    mounted() {
console.log(this.$route.params.id);
      this.$axios.get(`/api/jenis_surat/${this.$route.params.id}`)
        .then(response => {
            this.jenis_surat.jenis_surat   = response.data.data.jenis_surat,
            this.$axios.get('/api/jenis_surat')
            .then(response => {
              this.jenis_surat = response.data.data;
            })
            .catch(error => {
              console.log(error.response.data)
            })
        })
    },
    methods: {
      async update(e) {
        e.preventDefault()
        await this.$axios.put(`/api/jenis_surat/${this.$route.params.id}`, {
            //data yang dikirim
            jenis_surat:   this.jenis_surat.jenis_surat
          })
          .then(() => {
            this.$router.push({
              jenis_surat: 'jenis_surat'
            })
          })
          .catch(error => {
            this.validation = error.response.data
          })
      }
    }
  }
</script>

<style>
</style>
