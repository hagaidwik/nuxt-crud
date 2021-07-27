<template>
  <div>
    <div>
      <b-navbar
        toggleable="lg"
        type="light"
        variant="light"
        class="shadow-md"
        fixed="top"
      >
        <b-navbar-brand to="/">NUXT CRUD</b-navbar-brand>

        <b-navbar-toggle target="nav-collapse"></b-navbar-toggle>

        <!-- <b-collapse id="nav-collapse" is-nav>
          <b-navbar-nav>
            <b-nav-item to="/provinsi">Provinsi</b-nav-item>
            <b-nav-item to="/kabupaten">Kabupaten</b-nav-item>
            <b-nav-item to="/desa">Desa</b-nav-item>
          </b-navbar-nav>
        </b-collapse> -->
        <div>
          <b-nav pills>
            <b-nav-item-dropdown
              id="my-nav-dropdown"
              text="Data"
              toggle-class="nav-link-custom"
              right
            >
              <b-dropdown-item to="/provinsi">Provinsi</b-dropdown-item>
              <b-dropdown-item to="/kabupaten">Kabupaten</b-dropdown-item>
              <b-dropdown-item to="/kota">Kota</b-dropdown-item>
              <b-dropdown-item to="/kecamatan">Kecamatan</b-dropdown-item>
              <b-dropdown-divider></b-dropdown-divider>
              <b-dropdown-item>Three</b-dropdown-item>
            </b-nav-item-dropdown>
            <b-nav-item to="/desa">Desa</b-nav-item>
            <b<b-nav-item to="/jenis_Surat">jenis surat</b-nav-item>
          </b-nav>
        </div>
      </b-navbar>
    </div>

    <Nuxt />
  </div>
</template>

<style>
body {
  background-color: lightgray;
}
.mt-5 {
  margin-top: 100px !important;
}
</style>
