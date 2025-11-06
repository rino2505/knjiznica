<template>
  <q-page padding>
    <h4>Ovo je test1page</h4>
    <div class="q-pa-md q-gutter-sm">
    <q-btn push color="white" text-color="primary" label="Unread Mails">
      <q-badge color="orange" v-model="unread" floating>{{unread}}</q-badge>
    </q-btn>

    <q-btn dense color="purple" round icon="email" class="q-ml-md">
      <q-badge color="red" v-model="open" floating>{{open}}</q-badge>
    </q-btn>
  </div>
    <div class="q-pa-md q-gutter-sm">
    <q-card class="my-card bg-secondary text-white" v-for="item in msg" :key="item">
      <q-card-section>
        <div class="text-h6">{{item.title}}</div>
        <div class="text-subtitle2">{{item.author}}</div>
      </q-card-section>
      <q-card-section>
        {{ item.lorem }}
      </q-card-section>
       <q-separator dark />
      <q-card-actions>
        <q-btn flat @click="openMsg()">Uključ</q-btn>
        <q-btn flat @click="deleteMsg()">Isključ</q-btn>
      </q-card-actions>

      </q-card>
    </div>
    <div class="q-pa-md row items-start q-gutter-md">
      <q-input v-model="title" label="Title"/>
      <q-input v-model="author" label="Author"/>
      <q-input v-model="lorem" label="lorem"/>
      <q-btn flat @click="save()">Save</q-btn>
    </div>
  </q-page>
</template>

<script setup>
import { ref } from 'vue'
const msg = [
  {
  title:'Pater noster',
  author:'Jesus Christ',
  lorem:'Páter nóster, qui es in cáelis, sanctificétur nómen túum. Advéniat régnum túum. Fíat volúntas túa, sícut in cáelo et in térra. Pánem nóstrum quotidiánum da nóbis hódie, et dimítte nóbis débita nóstra sícut et nos dimíttimus debitóribus nóstris. Et ne nos indúcas in tentatiónem: sed líbera nos a málo. Amen'
  },
  {
    title:'Ave Maria',
    author:'Lk, Anđeo Gabrijel',
    lorem:'Ave Maria, gratia plena, Dominus tecum. Benedicta tu in mulieribus, et benedictus fructus ventris tui, Iesus. Sancta Maria, Mater Dei, ora pro nobis peccatoribus, nunc, et in hora mortis nostrae. Amen'
  }
]

let unread = ref (22)
let open = ref (4)

let title=ref('')
let author=ref('')
let lorem=ref('')

function openMsg(){
  open.value -= 1
  console.log("Uključ"+open.value)

}
function deleteMsg(){
  unread.value -=1
  console.log("Isključ"+unread.value)
}
function save()
{
  msg.push({title:title.value,author:author.value,lorem:lorem.value})
  console.log(msg)
}
</script>
<style lang="sass" scoped>
.my-card
  width: 100%
  max-width: 250px
</style>