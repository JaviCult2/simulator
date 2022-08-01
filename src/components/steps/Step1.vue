<template>

  <section class="mt-3">

    <v-form v-model="valid" ref="form">

      <div class="row">

        <div class="col-12  py-0">
          <v-text-field
              label="Nombre"
              v-model="user.name"
              :rules="rules.name"
              required
              dense
              solo
          ></v-text-field>
        </div>

        <div class="col-12 col-sm-6 py-0">
          <v-text-field
              label="Apellido Paterno"
              v-model="user.first_last_name"
              :rules="rules.last_name"
              required
              dense
              solo
          ></v-text-field>
        </div>

        <div class="col-12 col-sm-6 py-0">
          <v-text-field
              label="Apellido Materno"
              v-model="user.second_last_name"
              :rules="rules.last_name"
              pattern="\d*"
              type="number"
              required
              dense
              solo
          ></v-text-field>
        </div>

        <div class="col-12 col-sm-6 py-0">
          <v-text-field
              label="Teléfono"
              v-model="user.phone"
              :rules="rules.phone"
              pattern="\d*"
              type="number"
              required
              dense
              solo
          ></v-text-field>
        </div>

        <div class="col-12 col-sm-6 py-0">
          <v-text-field
              label="Correo"
              v-model="user.email"
              :rules="rules.email"
              required
              dense
              solo
          ></v-text-field>
        </div>

      </div>

    </v-form>

    <div class="row">
      <p class="text-center secondary-text">o carga tu INE y ahórrate tiempo</p>
    </div>

    <div class="text-center">
      <v-btn
          :loading="loading"
          elevation="2"
          class="btn-blue"
          v-on:click="validateData"
      >
        <font-awesome-icon icon="fa-solid fa-camera"/>
        <span class="ml-1 btn-text secondary-text">Frente</span>
      </v-btn>
    </div>

    <p class="text-center simple-text">
      <font-awesome-icon icon="fa-solid fa-eye"/>
      ¿Por qué te pedimos esta información?
    </p>

    <div class="text-center">
      <v-btn
          :loading="loading"
          elevation="2"
          class="btn-green"
          v-on:click="validateData"
      >
        <span class="btn-text secondary-text">Siguiente</span>
      </v-btn>
    </div>

  </section>

</template>

<script>
export default {
  name: "Step1",
  data: () => ({

    valid: false,
    loading: false,

    user:
        {
          name: null,
          first_last_name: null,
          second_last_name: null,
          phone: null,
          email: null,
        },

    rules:
        {
          name: [v => !!v || 'El nombre es requerido'],
          last_name: [v => !!v || 'El apellido es requerido'],
          phone:
              [
                v => !!v || 'El teléfono es requerido',
                v => /^([0-9]{10,13})$/.test(v) || 'Min: 10 - Max 13, dígitos'
              ],
          email:
              [
                v => !!v || 'El correo es requerido',
                v => /.+@.+/.test(v) || 'Formato invalido'
              ]
        }
  }),
  methods:
      {
        validateData() {
          this.loading = true

          if (this.$refs.form.validate()) {
            this.saveGeneralData()
          } else {
            console.log("Info incompleta")
          }

          this.loading = false
        },
        saveGeneralData() {

        }
      },
}
</script>

<style scoped>

</style>