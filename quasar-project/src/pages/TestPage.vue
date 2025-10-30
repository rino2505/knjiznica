<template>
  <q-page padding>
    <!-- content -->

    <h1>{{ porukica }}</h1>
    <p v-html="poruka"></p>
    <p v-html="htmlText"></p>
    <p v-text="htmlText"></p>
    <p v-for="item in days" :key="item">
      <button v-if="item=='Nedjelja'">
        {{ item }}*
      </button>
      <button v-else v-show="false">
        {{ item }}
      </button>
    </p>

  </q-page>
</template>

<script setup>
const porukica="Guten tag, wie geht es Ihnen?"
const poruka='Danke, gut. UND IHNEN?'
const htmlText="<p><b>Formatirani tekst </b></p>"
const days=["Ponedjeljak","Utorak","Srijeda","Četvrtak","Petak","Subota","Nedjelja"]
</script>
