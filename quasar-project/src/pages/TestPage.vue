<template>
  <q-page padding>
    <!-- content -->
    <a :href="link.url" :target="link.target">{{ link.text }}</a>
    <q-input color="green" v-model="text1" label="Item name" @keyup="log()"> </q-input>
    <q-input color="red" v-model="text1" label="Naziv" @keyup="log()"></q-input>
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
  import {ref} from 'vue'
  const text1=ref('')
  const text2=ref('')
  text1.value='Hello'
  const link ={
    url:'https://google.com',
    target:'_blank',
    text:'Google'
  };
  const porukica="Guten tag, wie geht es Ihnen?"
  const poruka='Danke, gut. UND IHNEN?'
  const htmlText="<p><b>Formatirani tekst </b></p>"
  const days=["Ponedjeljak","Utorak","Srijeda","Četvrtak","Petak","Subota","Nedjelja"]
  function log(){
    console.log(text1.value)
    console.log(text2.value)
  }
</script>
