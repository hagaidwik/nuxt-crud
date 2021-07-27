<template>
  <b-container fluid="md" class="mt-5 mb-5">
    <b-row>
      <b-col md="12">
        <b-card class="shadow-md border-0 rounded-lg">
          <h5>Tambah jenis surat</h5>
          <hr />
          <b-form @submit="store">
            <b-form-group label="desa">
              <b-form-select
                v-model="jenis_surat.id_desa"
                :options="desa"
                value-field="id"
                text-field="jenis_surat"
              ></b-form-select>
              <div v-if="validation.jenis_surat" class="mt-2">
                <b-alert show variant="danger">{{
                  validation.jenis_surat[0]
                }}</b-alert>
              </div>
            </b-form-group>

          

            <b-form-group label="jenis surat">
              <b-form-input
                type="text"
                v-model="jenis_surat.jenis_surat"
                :class="{ 'is-invalid': validation.title }"
                placeholder="jenis surat"
              >
              </b-form-input>
              <div v-if="validation.desa" class="mt-2">
                <b-alert show variant="danger">{{
                  validation.jenis_surat[4]
                }}</b-alert>
              </div>
            </b-form-group>
            <b-button type="submit" variant="primary">SIMPAN</b-button>
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
      //state post
      desa: [],
      jenis_surat: {
        id_desa: "",
        jenis_surat: "",
      },
      //state validation
      validation: [],
      selected: null
    };
  },

  mounted() {
    this.$axios
      .get("/api/desa")
      .then(response => {
        this.desa = response.data.data;
      })
      .catch(error => {
        console.log(error.response.data);
      });
  },

  methods: {
    async store(e) {
      e.preventDefault();
      await this.$axios
        .post("/api/jenis_surat", {
          //data yang dikirim ke server
          id_desa: this.jenis_surat.id_desa,
          jenis_surat: this.jenis_surat.jenis_surat,
        })
        .then(() => {
          //redirect ke route "post"
          this.$router.push({
            name: "jenis_surat"
          });
        })
        .catch(error => {
          //assign validation
          this.validation = error.response.data;
        });
    }
  }
};
</script>

<style></style>
