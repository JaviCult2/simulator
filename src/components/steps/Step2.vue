<template>

  <section class="mt-3">

    <v-form v-model="valid" ref="form">

      <div class="row">

        <div class="col-12 col-sm-4 py-0">
          <v-text-field
              label="Código Postal"
              v-model="user.postal_code"
              :rules="rules.postal_code"
              required
              dense
              solo
          ></v-text-field>
        </div>

        <div class="col-12 col-sm-8 py-0">
          <v-text-field
              label="Estado"
              v-model="user.state"
              :rules="rules.state"
              required
              dense
              solo
          ></v-text-field>
        </div>

        <div class="col-12 col-sm-6 py-0">
          <v-text-field
              label="Municipio"
              v-model="user.town"
              :rules="rules.town"
              pattern="\d*"
              type="number"
              required
              dense
              solo
          ></v-text-field>
        </div>

        <div class="col-12 col-sm-6 py-0">
          <v-text-field
              label="Colonia"
              v-model="user.suburb"
              :rules="rules.suburb"
              pattern="\d*"
              type="number"
              required
              dense
              solo
          ></v-text-field>
        </div>

        <div class="col-12 col-sm-8 py-0">
          <v-text-field
              label="Calle"
              v-model="user.street"
              :rules="rules.street"
              required
              dense
              solo
          ></v-text-field>
        </div>

        <div class="col-12 col-sm-4 py-0">
          <v-text-field
              label="Número"
              v-model="user.number"
              :rules="rules.number"
              required
              dense
              solo
          ></v-text-field>
        </div>

      </div>

    </v-form>

    <div class="text-center">
      <v-btn
          :loading="loading"
          elevation="2"
          class="btn-green"
          v-on:click="validateData"
      >
        <span class="btn-text secondary-text">Ver propuesta</span>
      </v-btn>
    </div>

  </section>

</template>

<script>
export default {
  name: "Step2",
  data: () => ({

    valid: false,
    loading: false,

    user:
        {
          postal_code: null,
          state: null,
          town: null,
          suburb: null,
          street: null,
          number: null,
        },

    rules:
        {
          postal_code:
              [
                v => !!v || 'El código postal es requerido',
                v => /^([0-9]{5})$/.test(v) || 'El código postal consta de 5 dígitos'
              ],
          state: [v => !!v || 'El estado es requerido'],
          town: [v => !!v || 'La ciudad es requerida'],
          suburb: [v => !!v || 'La colonia es requerida'],
          street: [v => !!v || 'La calle es requerida'],
          number:
              [
                v => !!v || 'El número es requerido',
                v => /^([0-9]{1,6})$/.test(v) || 'Mínimo 1 dígito - máximo 6 dígitos'
              ],
        }
  }),
  methods:
      {
        validateData() {
          this.loading = true

          if (this.$refs.form.validate()) {
            this.saveAddressData()
          } else {
            console.log("Info incompleta")
          }

          this.loading = false
        },

        saveAddressData() {

        }
      }
}
</script>

<style scoped>

</style>