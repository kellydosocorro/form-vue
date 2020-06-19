<template>
  <div id="app">
    <b-navbar toggleable="sm" type="dark" variant="danger" id="nav">
      <b-navbar-brand>
        <b-navbar-toggle target="nav-text-collapse" id="toggleable-button"></b-navbar-toggle>
        <router-link to="/">
          <img src="../public/images/ifood-logo.png" width="100"/>
        </router-link>
        <b-nav-text id="desktop-text" class="nav-text">para Restaurantes</b-nav-text>
      </b-navbar-brand>

      <b-collapse id="nav-text-collapse" is-nav>
        <b-navbar-nav class="ml-auto">
          <b-nav-text id="mobile-text" class="nav-text">para Restaurantes</b-nav-text>
          <b-button-group>
            <b-button squared variant="outline-light">
              Cadastrar
            </b-button>
            <b-button squared variant="outline-light">Entrar</b-button>
          </b-button-group>
        </b-navbar-nav>
      </b-collapse>
    </b-navbar>
    <router-view />
  </div>
</template>
