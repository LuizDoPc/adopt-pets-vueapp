<template>
  <div class="home">
    <h1>Adopt a new best friend.</h1>
    <h2>{{getAllCats.length}} cats</h2>
    <h2>{{ animalsCount }} pets</h2>
    <button class="btn btn-primary" @click="togglePetForm"> Add New Pet </button>

    <b-form @submit.prevent="handleSubmit" v-if="showPetForm">
      <b-form-group id="input-group-2" label="Pet's Name:" label-for="input-2">
        <b-form-input
          id="input-2"
          v-model="formData.name"
          required
          placeholder="Enter name"
        ></b-form-input>
      </b-form-group>

      <b-form-group id="input-group-3" label="Species:" label-for="input-3">
        <b-form-select
          id="input-3"
          v-model="formData.species"
          :options="['cats', 'dogs']"
          required
        ></b-form-select>
      </b-form-group>

      <b-form-group id="input-group-4" label="Pet's Age:" label-for="input-4">
        <b-form-input
          id="input-4"
          type="number"
          v-model="formData.age"
          required
          placeholder="Enter age"
        ></b-form-input>
      </b-form-group>

      <b-form-group id="input-group-5" label="Pet's Breed:" label-for="input-5">
        <b-form-input
          id="input-5"
          v-model="formData.breed"
          required
          placeholder="Enter breed"
        ></b-form-input>
      </b-form-group>

      <b-form-group id="input-group-6" label="Pet's Gender:" label-for="input-6">
        <b-form-input
          id="input-6"
          v-model="formData.gender"
          required
          placeholder="Enter gender"
        ></b-form-input>
      </b-form-group>

      <b-form-group id="input-group-7" label="Pet's Color:" label-for="input-7">
        <b-form-input
          id="input-7"
          v-model="formData.color"
          required
          placeholder="Enter color"
        ></b-form-input>
      </b-form-group>

      <b-form-group id="input-group-8" label="Pet's Weight:" label-for="input-8">
        <b-form-input
          id="input-8"
          v-model="formData.weight"
          required
          placeholder="Enter weight"
        ></b-form-input>
      </b-form-group>

      <b-form-group id="input-group-9" label="Pet's Location:" label-for="input-9">
        <b-form-input
          id="input-9"
          v-model="formData.location"
          required
          placeholder="Enter location"
        ></b-form-input>
      </b-form-group>

      <b-form-group id="input-group-10" label="Pet's Notes:" label-for="input-10">
        <b-form-input
          id="input-10"
          v-model="formData.notes"
          required
          placeholder="Enter notes"
        ></b-form-input>
      </b-form-group>

      <b-button type="submit" variant="primary">Submit</b-button>
    </b-form>
  </div>
</template>

<script>
import { mapActions, mapGetters } from 'vuex'

export default {
  name: 'home',
  data () {
    return {
      showPetForm: false,
      formData: {
        name: '',
        age: 0,
        species: null,
        breed: '',
        gender: '',
        color: '',
        weight: 0,
        location: '',
        notes: ''
      }
    }
  },
  computed: {
    ...mapGetters([
      'animalsCount',
      'getAllCats'
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
      const { species } = this.formData
      this.addPet({ species, pet: this.formData })

      this.formData = {
        name: '',
        age: 0,
        species: null,
        breed: '',
        gender: '',
        color: '',
        weight: 0,
        location: '',
        notes: ''
      }
    }
  }
}
</script>
