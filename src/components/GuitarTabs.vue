<template>
  <div>
    <div class="tab-container">
      <div v-for="section in sections">
        <h1>{{section.name}}</h1>
        <table class="tuning">
          <tr v-for="key in section.tuning">
            <td>{{key}}</td>
          </tr>
        </table>

        <table class="tabs" v-for="measure in section.measures">
          <tr class="keys">
            <td v-for="key in measure.keys">
              {{key}}
            </td>
          </tr>
          <tr v-for="string in measure.notes">
            <td v-for="note in string">
              <span class="note" :class="{empty: note === '', x: note === 'x'}">{{note}}</span>
            </td>
          </tr>
        </table>
      </div>
    </div>
  </div>
</template>

<script>

export default {
  props: [
    'sections'
  ]
}
</script>

<style scoped>
.tab-container {
  width: 600px;
  margin: 0 auto;
  color: white;
}

table.tuning {
  display: inline-block;
  border-collapse: collapse;
  vertical-align: top;
  margin-right: 10px;
  font-weight: bold;
  font-size: 20px;
  padding-top: 60px;
}

table.tuning td {
  height: 44px;
  line-height: 44px;
}

table.tabs .keys {
  position: relative;
}

table.tabs .keys td {
  border-bottom: none;
  position: relative;
  top: 24px;
}

table.tabs {
  vertical-align: top;
  position: relative;
  display: inline-block;
  border-collapse: collapse;
  margin-bottom: 30px;
}

table.tabs::after {
  content: '';
  border-right: 1px solid white;
  height: 239px;
  display: inline-block;
  position: absolute;
  top: 87px;
  right: 0px;
}

table.tabs td {
  height: 44px;
}

table.tabs .note {
  display: inline-block;
  width: 24px;
  height: 24px;
  text-align: center;
  line-height: 24px;
  border-radius: 50%;
  background-color: #853962;
  color: white;
  font-weight: bold;
  position: relative;
  top: 22px;
  margin-right: 10px;
  margin-left: 10px;
}

table.tabs .note.empty {
  opacity: 0;
}

table.tabs .note.x {
  background-color: inherit;
  border: none;
  font-size: 30px;
  font-weight: normal;
  color: #853962;
}

table.tabs td {
  border-bottom: 1px solid white;
  padding: 0;
  margin: 0;
}
</style>
