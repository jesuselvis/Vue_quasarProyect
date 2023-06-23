<template>
  <p-page>
    <pre>{{productos}}</pre>
    
    <q-table
      title="Productos en stock"
      class="q-mt-sm"
      no-data-label="Tabla vacio, sin datos actuales"
      :columns="columns"
      :rows="productos"

    />
  </p-page>
</template>

<script>

const columns =[
  {
    name: 'producto',
    label: 'Producto',
    align: 'left',
    field: 'producto',
    sortable: true
  },
  {
    name: 'prioridad',
    label: 'Prioridad',
    align: 'left',
    field: 'prioridad',
    sortable: true
  }

]

const rows=[
   {
    producto: 'producto 1',
    prioridad: 'maxima'
   }

]

export default {
  // name: 'ComponentName',
  props:{
    productos: Array
  },
  setup () {
    return {
      columns,
      rows
    }
  }
}
</script>
