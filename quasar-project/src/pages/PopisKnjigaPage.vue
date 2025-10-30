<template>
  <div class="q-pa-md">
    <q-table
      title="Knjige"
      :rows="rows"
      :columns="columns"
      row-key="name"
    />
  </div>
</template>

<script>
const columns = [
  {
    name: 'name',
    required: true,
    label: 'Naslov knjige',
    align: 'left',
    field: row => row.name,
    format: val => `${val}`,
    sortable: true
  },
  { name: 'id', align: 'center', label: 'ID knjige', field: 'id', sortable: true },

  { name: 'autor', label: 'Autor knjige', field: 'autor' },
  { name: 'opis', label: 'Opis knjige', field: 'opis' },
  { name: 'slika', label: 'Slika knjige', field: 'slika' },
  { name: 'stanje', label: 'Stanje', field: 'stanje'},
]

const rows = [
  {
    name: 'The Very Hungry Caterpillar',
    id: 1,
    autor: 'Eric carle',
    opis:'As an added bonus, it includes read-aloud audio of Eric Carle reading his classic story.',
    slika: 'nema slike',
    stanje:3
  },
  {
    name: 'Palace of Palms: Tropical Dreams and the Making of Kew',
    id: 2,
    autor: 'Kate Teltscher',
    opis:'The body is assaulted by heat, light and the smell of damp vegetation.',
    slika: 'nema slike',
    stanje:3
  },
]

export default {
  setup () {
    return {
      columns,
      rows
    }
  }
}
</script>
