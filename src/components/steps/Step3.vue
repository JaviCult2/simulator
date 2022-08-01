<template>

  <v-card elevation="24" class="mx-auto">

    <v-system-bar lights-out></v-system-bar>

    <v-carousel
        height="250"
        delimiter-icon="mdi-minus"
        hide-delimiter-background
    >
      <v-carousel-item
          v-for="(item, index) in debts"
          :key="index"
      >
        <v-sheet
            height="100%"
            tile
        >
          <v-row
              class="fill-height"
              align="center"
              justify="center"
          >

            <v-card elevation="0" min-height="250px">
              <v-card-text>
                <div class="row">

                  <div class="col-10 mx-auto text-center">
                    <img :src="item.imgBank" :alt="item.bank" width="30%">
                  </div>

                  <div class="d-flex justify-content-between">
                    <p>Banco:</p>
                    <p>{{ item.bank }}</p>
                  </div>

                  <div class="d-flex justify-content-between">
                    <p>Debes:</p>
                    <p>{{ item.debt }}</p>
                  </div>

                  <div class="d-flex justify-content-between">
                    <p>Con DBMenos paga:</p>
                    <p>{{ item.youWillPay }}</p>
                  </div>

                  <div class="d-flex justify-content-between">
                    <p>Descuento del:</p>
                    <p>{{ item.percent }}</p>
                  </div>

                </div>
              </v-card-text>
            </v-card>

          </v-row>
        </v-sheet>
      </v-carousel-item>
    </v-carousel>


    <v-list two-line>
      <v-list-item>
        <v-list-item-avatar>
          <v-img src="/images/icons/logo.png"></v-img>
        </v-list-item-avatar>
        <v-list-item-content>
          <v-list-item-title>DBMenos</v-list-item-title>
          <v-list-item-subtitle>Reparadora de crédito mexicana</v-list-item-subtitle>
        </v-list-item-content>
        <v-list-item-action>
          <v-btn
              elevation="2"
              class="btn-green"
              :loading="loading"
              v-on:click="saveUser"
          >
            <font-awesome-icon icon="fa-solid fa-circle-check"/>
            <span class="ml-1 btn-text secondary-text">Lo quiero</span>
          </v-btn>
        </v-list-item-action>
      </v-list-item>
    </v-list>

  </v-card>

</template>

<script>
export default {
  name: "Step3",
  data: () => ({
    loading: false,

    debts:
        [
          {
            imgBank: '/images/banks/bbva.svg',
            bank: 'BBVA',
            debt: '500,000',
            youWillPay: '150,000',
            percent: '50%'
          },
          {
            imgBank: '/images/banks/santander.svg',
            bank: 'Santander',
            debt: '450,000',
            youWillPay: '200,000',
            percent: '70%'
          }
        ],
  }),
  methods:
      {
        saveUser() {

        }
      }
}
</script>

<style scoped>

</style>