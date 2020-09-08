<template>
  <div>
    <h1>{{species | capitalize}} For Adoption</h1>
    <b-table striped hover :items="pets">
      <template v-slot:cell(name)="data">
        <router-link :to="`/pets/${species}/${data.index}`">{{ data.value }}</router-link>
      </template>
    </b-table>
  </div>
</template>

<script>
export default {
  props: {
    species: String,
    pets: Array
  },
  filters: {
    capitalize: function (value) {
      console.log(value.charAt(0).toUpperCase() + value.slice(1))
      return value.charAt(0).toUpperCase() + value.slice(1)
    }
  }
}
</script>
