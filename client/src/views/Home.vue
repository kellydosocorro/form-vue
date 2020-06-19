<template>
  <div>
    <div id="wave"></div>
    <b-container fluid="md" class="bv-example-row">
      <b-row>
        <b-col id="formulario">
          <b-card img-alt="Image" img-top tag="article" class="main-card">
            <span class="anuncio">Seja um restaurante parceiro!</span>

            <b-form v-if="show">
              <b-form-group id="input-group-1" label="Nome Completo:" label-for="name">
                <b-form-input
                  id="name"
                  v-model="form.name"
                  required
                  placeholder="Digite seu nome completo"
                ></b-form-input>
              </b-form-group>

              <b-form-group id="input-group-2" label="E-mail:" label-for="email">
                <b-form-input
                  id="email"
                  v-model="form.email"
                  type="email"
                  required
                  placeholder="Digite o endereço de e-mail do seu negócio"
                ></b-form-input>
              </b-form-group>

              <b-form-group id="input-group-3" label="Nome da Empresa:" label-for="businessname">
                <b-form-input
                  id="businessname"
                  v-model="form.business_name"
                  required
                  placeholder="Digite o nome de sua empresa"
                ></b-form-input>
              </b-form-group>

              <b-form-group id="input-group-4" label="CNPJ:" label-for="cnpj">
                <b-form-input
                  id="cnpj"
                  type="number"
                  max="14"
                  v-model="form.cnpj"
                  placeholder="Digite o CNPJ da sua empresa"
                  description="O CNPJ deve possuir 14 números e deve ser digitado sem pontos, traços ou barras"
                  required
                ></b-form-input>
              </b-form-group>

              <b-form-group id="input-group-3" label="Tipo de negócio:" label-for="business-type">
                <b-form-select
                  id="business-type"
                  v-model="form.business_type"
                  :options="business"
                  required
                ></b-form-select>
              </b-form-group>

              <b-form-group id="input-group-5" label="Senha:" label-for="password">
                <b-form-input
                  id="password"
                  v-model="form.password"
                  placeholder="Digite uma senha para a sua conta"
                  type="password"
                  required
                ></b-form-input>
              </b-form-group>

              <b-button v-b-modal.modal-1 block variant="danger" size="lg">Solicitar cadastro</b-button>
              <b-modal id="modal-1" title="Cadastro Ifood">
                <div v-if="isNull()">
                  <p class="my-4"><b>Nome:</b> {{form.name}}</p>
                  <p class="my-4"><b>Senha:</b> {{ form.password }}</p>
                  <p class="my-4"><b>Empresa:</b> {{form.business_name}}</p>
                  <p class="my-4"><b>CNPJ:</b> {{ (form.cnpj).replace(/^(\d{2})(\d{3})(\d{3})(\d{4})(\d{2})/, "$1.$2.$3/$4-$5")}}</p>
                  <p class="my-4"><b>E-mail:</b> {{form.email}}</p>
                  <p class="my-4"><b>Tipo de negócio:</b> {{ form.business_type }}</p>
                </div>
                <div v-else>
                  <p class="my-4">Por favor, preencha os dados necessários.</p>
                </div>
              </b-modal>
            </b-form>
          </b-card>
        </b-col>
      </b-row>
      <b-row>
        <b-col style="text-align:center;font-size:0.6em;margin:10px 0px;">
          Design por <a href="https://github.com/kellydosocorro/">Kelly Costa</a>. Ilustração: <a href="https://br.freepik.com/" target="_blank">freepik</a>.
        </b-col>
      </b-row>
    </b-container>
  </div>
</template>

<script>
  export default {
    data() {
      return {
        form: {
          email: null,
          name: null,
          business_type: null,
          business_name: null,
          cnpj: null,
          password: null
        },
        business: [{ text: 'Escolha uma opção', value: null }, { text: 'Restaurante', value: 'Restaurante'}, { text: 'Mercado', value: 'Mercado' }, { text: 'Lanches e fast food', value: 'Lanches e fast food'}, { text: 'Doceria', value: 'Doceria'}],
        show: true
      }
    },
    methods: {
      onSubmit(evt) {
        evt.preventDefault()
        alert(JSON.stringify(this.form))
      },
      isNull() {
        if (this.form.email !== null && this.form.name !== null && this.form.business_type !== null && this.form.business_name !== null && this.form.business_type !== null && this.form.password !== null && (this.form.cnpj).length === 14) {
          return true
        }
        return false
      }
    }
  }
</script>
