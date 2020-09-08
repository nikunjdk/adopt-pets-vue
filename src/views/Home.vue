<template>
  <div class="home-view-container">
    <h1>Adopt A New best Friend</h1>
    <p>Number of Animals Up for Adoption: {{ animalsCount }}</p>
    <button @click="togglePetForm" class="btn btn-primary">Add A New Pet</button>
    <b-form @submit.prevent="handleSubmit" v-if="showPetForm">

      <b-form-group id="input-group-1" label="Name:" label-for="input-1">
        <b-form-input
          id="input-1"
          v-model="formData.name"
          required
          placeholder="Enter name"
        ></b-form-input>
      </b-form-group>

      <b-form-group id="input-group-2" label="Species:" label-for="input-2">
        <b-form-select
          id="input-2"
          v-model="formData.species"
          :options="['cat','dog']"
          required
        ></b-form-select>
      </b-form-group>

      <b-form-group id="input-group-3" label="Age:" label-for="input-3">
        <b-form-input
          id="input-3"
          v-model="formData.age"
          type="number"
          required
          placeholder="Enter Age"
        ></b-form-input>
      </b-form-group>

      <b-form-group id="input-group-4" label="Breed:" label-for="input-4">
        <b-form-input
          id="input-4"
          v-model="formData.breed"
          required
          placeholder="Enter Breed"
        ></b-form-input>
      </b-form-group>

      <b-form-group id="input-group-5" label="Gender:" label-for="input-5">
        <b-form-select
          id="input-5"
          v-model="formData.gender"
          :options="['male','female']"
          required
        ></b-form-select>
      </b-form-group>

      <b-form-group id="input-group-6" label="Color:" label-for="input-6">
        <b-form-input
          id="input-6"
          v-model="formData.color"
          required
          placeholder="Enter Color"
        ></b-form-input>
      </b-form-group>

      <b-form-group id="input-group-7" label="Weight:" label-for="input-7">
        <b-form-input
          id="input-7"
          v-model="formData.weight"
          type="number"
          required
          placeholder="Enter Weight"
        ></b-form-input>
      </b-form-group>

      <b-form-group id="input-group-8" label="Location:" label-for="input-8">
        <b-form-input
          id="input-8"
          v-model="formData.location"
          required
          placeholder="Enter Location"
        ></b-form-input>
      </b-form-group>

      <b-form-group id="input-group-9" label="Notes:" label-for="input-9">
        <b-form-input
          id="input-9"
          v-model="formData.notes"
          required
          placeholder="Enter Notes"
        ></b-form-input>
      </b-form-group>

      <b-button type="submit" variant="primary">Submit</b-button>
      <b-button type="reset" variant="danger">Reset</b-button>
    </b-form>
  </div>
</template>

<script>
import { mapActions, mapGetters } from 'vuex'
export default {
  data () {
    return {
      showPetForm: false,
      formData: {
        name: '',
        age: 0,
        species: null,
        breed: '',
        gender: null,
        color: '',
        weight: 0,
        location: '',
        notes: ''
      }
    }
  },
  computed: {
    ...mapGetters([
      'animalsCount'
    ])
  },
  methods: {
    ...mapActions([
      'addPet'
    ]),
    togglePetForm () {
      this.showPetForm = !this.showPetForm
    },
    handleSubmit () {
      const { species, age, name, breed, gender, color, weight, location, notes } = this.formData
      const payload = {
        species,
        pet: {
          name,
          age,
          breed,
          gender,
          color,
          weight,
          location,
          notes
        }
      }
      this.addPet(payload)
      this.formData = {
        name: '',
        age: 0,
        species: null,
        breed: '',
        gender: null,
        color: '',
        weight: 0,
        location: '',
        notes: ''
      }
    }
  }
}
</script>

<style scoped>
  .btn {
    margin: 0px 5px;
  }
</style>
