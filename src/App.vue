<script setup lang="ts">
import { computed } from 'vue'

interface ISite {
  name?: string
  url: string
}

const sites = computed(() => {
  return [
    {
      name: 'Mercado Livre',
      url: 'https://www.mercadolivre.com.br/presentes/isabel-e-edson-00vgu',
    },
  ] as Array<ISite>
})

const openSite = (site: ISite) => {
  const a = document.createElement('a')
  a.href = site.url
  a.target = '_blank'
  a.click()
}
const confirmUrl: ISite = {
  url: 'https://wa.me/5515991157834?text=Ol%C3%A1%20Lucas%2C%20tudo%20bem%3F%0AClaro%20que%20eu%20vou%2C%20pode%20me%20confirmar%2C%20estarei%20la%2C%20obrigado%20pelo%20convite!',
}
const disconfirmUrl: ISite = {
  url: 'https://wa.me/5515991157834?text=Ol%C3%A1%20Lucas%2C%20tudo%20bem%3F%0AInfelizmente%20n%C3%A3o%20irei%20conseguir%20ir%2C%20mas%20muito%20obrigado%20pelo%20convite',
}
</script>

<template>
  <header>
    <img alt="Casamento data" class="logo mb-32" src="@/assets/logo.png" width="200" height="200" />
    <div class="title mb-32">
      Isabel <span style="color: var(--color-brown-light)">&</span> Edson
    </div>
  </header>

  <section class="description mb-32">
    <b style="font-weight: bold !important">Olá, queridos amigos e familiares!</b>
    <br />
    <br />
    <p>
      Estamos muito feliz em poder compartilhar este momento tão especial com cada um de vocês. Para
      nós, é uma grande alegria saber que vocês estarão ao nosso lado nesse momento!
    </p>
    <p>Agradecemos profundamente por todo apoio e por sempre estarem presente em nossas vidas.</p>
    <p>
      Para que tudo seja preparado com carinho e cuidado, pedimos que confirme sua presença até
      <b style="font-weight: bold">21/04/2025</b>.
    </p>
    <br />
    <p><b>👉 Confirme sua presença clicando aqui:</b></p>
    <br />
    <div>
      <button class="button" @click="openSite(confirmUrl)">Eu vou 🎉</button>
      <button class="button" @click="openSite(disconfirmUrl)">Não conseguirei ir 😔</button>
    </div>
  </section>
  <br />
  <br />
  <section>
    <div class="title mb-32">Lista de presente</div>
    <p class="description mb-32">
      Caso queira presentea-los, abaixo terá uma lista de presentes que escolhemos com muito carinho
      e que eles com certeza irão adorar.
    </p>
    <button v-for="(site, i) in sites" :key="`site-${i}`" class="button" @click="openSite(site)">
      Acessar lista 🎁
    </button>
  </section>

  <img class="footer" src="@/assets/footer.png" width="100%" />
</template>

<style scoped lang="sass">
header
  line-height: 1.5
  max-height: 100vh

.logo
  display: block
  margin: auto

.mb-32
  margin-bottom: 32px

.title
  font-family: Baskervville !important
  color: var(--color-green) !important
  font-size: 42px
  text-align: center

.description
  font-size: 14px
  text-align: center
  max-width: 450px
  margin-left: auto
  margin-right: auto

.button
  background: var(--color-green-light)
  border: 0px
  height: 48px
  border-radius: 8px
  display: block
  width: 100%
  max-width: 450px
  margin: auto
  margin-bottom: 24px
  color: white
  font-weight: bold
  font-size: 15px
  font-family: 'Open Sans' !important
  cursor: pointer
  &:hover
    background: var(--color-green)

.pix-container
  background: white
  width: 200px
  height: 200px
  margin: 0 auto
  margin-bottom: 32px

@media screen and (max-width: 500px)
  .footer
    position: relative
    width: 100vw
    margin-left: -2rem
    margin-bottom: -2.2rem
    margin-top: -2rem
</style>
