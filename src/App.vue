<template>
  <div>
    <div id="app" ref="spreadsheet"></div>
    <div><input type="button" value="Add new row" @click="() => spreadsheet.insertRow()" /></div>
  </div>
</template>

<script>
import jexcel from 'jexcel'
import 'jexcel/dist/jexcel.css'

var data = [
  ['Jazz', 'Honda', '2019-02-12', '', true, '$ 2.000,00', '#777700'],
  ['Civic', 'Honda', '2018-07-11', '', true, '$ 4.000,01', '#007777']
]

var options = {
  data: data,
  allowToolbar:true,
  columns: [
    { type: 'text', title: 'Car', width: '120px' },
    { type: 'dropdown', title: 'Make', width: '250px', source: [ 'Alfa Romeo', 'Audi', 'Bmw' ] },
    { type: 'calendar', title: 'Available', width: '250px' },
    { type: 'image', title: 'Photo', width: '120px' },
    { type: 'checkbox', title: 'Stock', width: '80px' },
    { type: 'numeric', title: 'Price', width: '100px', mask: '$ #.##,00', decimal: ',' },
    { type: 'color', width: '100px', render: 'square' }
  ]
}

export default {
  name: 'App',
  mounted: function () {
    let spreadsheet = jexcel(this.$el, options)
    Object.assign(this, { spreadsheet })
  }
}
</script>
