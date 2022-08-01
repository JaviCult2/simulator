<template>

  <div class="bg-principal">

    <div class="row col-12 col-sm-7 mx-auto bg-form">

      <p class="text-center title-text">
        Te ayudamos a liquidar tus deudas <br>
        hasta con un 70% de descuento.
      </p>

      <v-stepper v-model="step" elevation="5" style="border-radius: 1rem">

        <p class="text-center primary-text">
          Calcula tu plan <br> personalizado en 3 pasos
        </p>

        <v-stepper-header class="shadow-none">
          <v-stepper-step :complete="step > 1" step="1" @click="step=1">
            <span class="simple-text">Datos generales</span>
          </v-stepper-step>

          <v-divider></v-divider>

          <v-stepper-step :complete="step > 2" step="2" @click="step=2">
            <span class="simple-text">Datos domiciliares</span>
          </v-stepper-step>

          <v-divider></v-divider>

          <v-stepper-step step="3" @click="step=3">
            <span class="simple-text">Propuesta</span>
          </v-stepper-step>
        </v-stepper-header>

        <v-stepper-items>
          <v-stepper-content step="1">
            <v-card
                class=""
                color="#EBEDEF"
            >
              <v-card-text>
                <step1/>
              </v-card-text>
            </v-card>
          </v-stepper-content>

          <v-stepper-content step="2">
            <v-card
                class=""
                color="#EBEDEF"
            >
              <v-card-text>
                <step2/>
              </v-card-text>
            </v-card>
          </v-stepper-content>

          <v-stepper-content step="3">
            <v-card
                class=""
                color="#EBEDEF"
            >
              <v-card-text>
                <step3/>
              </v-card-text>
            </v-card>
          </v-stepper-content>
        </v-stepper-items>
      </v-stepper>

    </div>

  </div>

</template>

<script>
import Step1 from "@/components/steps/Step1";
import Step2 from "@/components/steps/Step2";
import Step3 from "@/components/steps/Step3";

export default {
  name: "Principal",
  components: {Step3, Step2, Step1},
  data: () => ({
    step: 1,
  }),
  methods:
      {}
}
</script>

<style scoped>


</style>