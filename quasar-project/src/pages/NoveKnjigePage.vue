<template>
  <q-page padding>

    <q-toolbar class="bg-red-9 text-yellow">
      <q-toolbar-title>
        Nove knjige
      </q-toolbar-title>
    </q-toolbar>
   <div class="q-pa-md row items-start q-gutter-md">
    <q-card class="my-card">
      <img src="https://ezop-antikvarijat.hr/wp-content/uploads/2020/10/products-0a3bd4bac496b44163e2ef5d20283066.jpg" alt="Vlak u Sniejgu">

      <q-card-section>
        <div class="text-h6">Vlak u Snijegu</div>
        <div class="text-subtitle2">Autor: Mato Lovrak</div>
      </q-card-section>

      <q-card-section class="q-pt-none">
        {{ VuS }}
      </q-card-section>
    </q-card>
    <q-card class="my-card">
      <img src="https://knjiga-znanja-veda.hr/images/slike-stari-web/1386.jpg" alt="U registarturi">

      <q-card-section>
        <div class="text-h6">U registarturi</div>
        <div class="text-subtitle2"> Ante Kovačić</div>
      </q-card-section>

      <q-card-section class="q-pt-none">
        {{ UR }}
      </q-card-section>
    </q-card>
    <q-card class="my-card">
      <img src="https://www.zagrebacka-stvarnost.hr/cdn/shop/products/skrtac_prava_1200x1200.jpg?v=1549900418" alt="Skrtac">

      <q-card-section>
        <div class="text-h6">Škrtac</div>
        <div class="text-subtitle2">Jean B. Moliere</div>
      </q-card-section>

      <q-card-section class="q-pt-none">
        {{ S1 }}
      </q-card-section>
    </q-card>
    </div>
  </q-page>
</template>
<script>
export default {
  setup () {
    return {
      VuS: '"Vlak u snijegu" je dječji roman hrvatskog književnika Mate Lovraka, napisan 1933. godine. To je jedno od najpoznatijih i najomiljenijih djela u hrvatskoj dječjoj književnosti, a obrađuje teme prijateljstva, složnosti i prevladavanja prepreka',
      UR: '"U registraturi" je najpoznatiji i najznačajniji roman hrvatskog pisca Ante Kovačića, objavljen 1888. godine u nastavcima u časopisu "Vijenac". Smatra se ključnim djelom hrvatskog realizma.',
      S1:'"Škrtac" je komedija francuskog dramatičara Molièrea, napisana 1668. godine. Smatra se jednim od najvećih djela komediografije i prikazuje vječnu temu pohlepe i škrtosti kroz lik starog Harpagona'
    }
  }
}
</script>

<style lang="sass" scoped>
.my-card
  width: 100%
  max-width: 250px
</style>

