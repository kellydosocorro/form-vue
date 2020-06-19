<template>
  <div>
    <div id="wave"></div>
    <b-container fluid="md" class="bv-example-row">
      <b-row>
        <b-col style="margin:50px 0px 20px 0px;">
          <b-card class="main-card">
            <span style="text-align:left!important;" class="anuncio">Empresas parceiras</span>

            <div class="row">
              <div v-for="(business, i) in all_business" :key="i" class="col-sm-4">
                <div class="card" style="margin-bottom:20px;">
                  <div class="card-header">
                    <h4 class="my-0 font-weight-normal">
                      {{business.name}}
                      </h4>
                    </div>
                  <div class="card-body">
                    <p class="my-4"><b>Empresa:</b> {{business.business_name}}</p>
                    <p class="my-4"><b>CNPJ:</b> {{ (business.cnpj).replace(/^(\d{2})(\d{3})(\d{3})(\d{4})(\d{2})/, "$1.$2.$3/$4-$5")}}</p>
                    <p class="my-4"><b>Tipo de negócio:</b> {{ business.business_type }}</p>
                  </div>
                </div>
              </div>
            </div>
          </b-card>
        </b-col>
      </b-row>
      <b-row>
        <b-col style="text-align:center;font-size:0.6em;margin:10px 0px;">
          Design por
          <a href="https://github.com/kellydosocorro/">Kelly Costa</a>. Ilustração:
          <a href="https://br.freepik.com/" target="_blank">freepik</a>.
        </b-col>
      </b-row>
    </b-container>
  </div>
</template>

<script>
import axios from 'axios'
  export default {
    name: 'AllBusiness',
    data() {
      return {
        all_business: []
      }
    },
    methods: {
      async getBusiness() {
        await axios.get('https://5eeca45a5e298b0016b69f88.mockapi.io/api/form-vue/business')
          .then(response => {
            console.log(response)
            this.all_business = response.data
          })
          .catch(({ response }) => {
            console.log(response.status)
          })
      }
    },
    created () {
      this.getBusiness()
    }
  }
</script>
