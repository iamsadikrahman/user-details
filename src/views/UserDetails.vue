<script setup>
import {ref, reactive, computed, watch} from 'vue';

const user = reactive({
  name: 'John Doe',
  email: 'john@example.com',
  avatar: 'https://images.unsplash.com/photo-1535713875002-d1d0cf377fde?ixlib=rb-4.0.3&ixid=MnwxMjA3fDB8MHxwaG90by1wYWdlfHx8fGVufDB8fHx8&auto=format&fit=crop&w=774&q=80',
  birthDate: '01/01/2000',
  description: 'I am a developer and I love to code web applications using Vue.js and Laravel with Tailwind CSS and Vuetify for frontend and Laravel Livewire for backend.',
  votingEligibilityMessage: '',

})


const name = ref('')
const email = ref('')
const avatar = ref('')
const birthDate = ref('')
const description = ref('')


// When user click update button then name and email will be updated

// if input is empty set before data
const updateDetails = () => {

  // Check if the input values are not empty before updating the user's properties
  if (name.value.trim() !== '') {
    user.name = name.value;
  }
  if (email.value.trim() !== '') {
    user.email = email.value;
  }
  if (avatar.value.trim() !== '') {
    user.avatar = avatar.value;
  }
  if (birthDate.value.trim() !== '') {
    user.birthDate = birthDate.value;
  }
  if (description.value.trim() !== '') {
    user.description = description.value;
  }


  name.value = ''
  email.value = ''
  avatar.value = ''
  birthDate.value = ''
  description.value = ''
}


// Create a computed property to calculate the user's birth year
const birthYear = computed(() => {
  return new Date(user.birthDate).getFullYear();
})

// Create a computed property to check if the user is of legal age for voting
const isLegalVoter = computed(() => {
  const birthYear = new Date(user.birthDate).getFullYear();
  const currentYear = new Date().getFullYear();
  const age = currentYear - birthYear;
  return age >= 18;
})


// Initialize the voting eligibility message based on the user's initial birth year
user.votingEligibilityMessage = birthYear.value >= 18 ? 'eligible for voting' : 'not eligible for voting';

// Create a watcher to monitor changes in the user's birth date
watch(() => user.birthDate, (newBirthDate) => {
  const birthYear = new Date(newBirthDate).getFullYear();
  user.votingEligibilityMessage = birthYear >= 18 ? 'eligible for voting' : 'not eligible for voting';
});


</script>

<template>
<div class="min-w-full min-h-screen my-14">
  <h1 class="text-3xl font-bold mb-10 text-center  ">User Details</h1>
  <section class="grid grid-cols-2 gap-8">
<!--    Personal Details-->
    <div class="flex flex-col items-center bg-white rounded shadow  space-y-5 p-12">
      <h2 class="text-2xl font-semibold -mt-8">Personal Details</h2>
      <img class="rounded-full w-56" :src="user.avatar" alt="Avatar">
      <h2 class=" text-2xl font-semibold">{{(name === "" ? user.name : user.name)}}</h2>
      <p class="text-gray-600 text-center">{{user.description}}</p>

    <!-- Birth Date, Email-->
      <div class="grid grid-cols-2 gap-8  items-center justify-center">
        <div class="flex flex-col items-center shadow rounded p-5 space-y-3">
          <h2 class=" text-2xl font-semibold">Birth Date</h2>
          <p class=" text-gray-600">{{user.birthDate}}</p>
        </div>
        <div class="flex flex-col items-center  shadow rounded p-5 space-y-3">
          <h2 class=" text-2xl font-semibold">Email</h2>
          <p class=" text-gray-600">{{user.email}}</p>
        </div>
        <!-- Display the user's birth year and voting eligibility status -->
        <div class="flex flex-col items-center shadow rounded p-5 space-y-3">
          <h2 class="text-2xl font-semibold">Birth Year</h2>
          <p class="text-gray-600">{{ birthYear }}</p>
        </div>

        <div class="flex flex-col items-center shadow rounded p-5 space-y-3">
          <h2 class="text-2xl font-semibold">Election Eligibility</h2>
          <p class="text-gray-600">{{ isLegalVoter ? 'You legally have the right to vote.' : 'You do not legally have the right to vote.' }}</p>
        </div>
        <div class="flex flex-col items-center shadow rounded p-5 space-y-3">
          <h2 class="text-2xl font-semibold">Voting Eligibility</h2>
          <p class="text-gray-600">{{ user.votingEligibilityMessage }}</p>
        </div>
      </div>
    </div>
<!--    Edit Details-->
    <div class="flex flex-col items-center bg-white rounded shadow space-y-5 p-14">
      <h2 class="text-2xl font-semibold -mt-8">Edit Details</h2>
      <form>
        <div class="flex flex-col space-y-3">
          <div class="flex flex-col space-y-1">
            <label for="name">Name</label>
            <input type="text" id="name" v-model="name" class="shadow appearance-none border rounded w-full py-2 px-3 text-gray-700 leading-tight focus:outline-none focus:shadow-outline" placeholder="Your Name">
          </div>
<!--          Edit Avatar Link-->
          <div class="flex flex-col space-y-1">
            <label for="avatar">Profile Picture (*URL)</label>
            <input type="text" id="avatar" v-model="avatar" class="shadow appearance-none border rounded w-full py-2 px-3 text-gray-700 leading-tight focus:outline-none focus:shadow-outline" placeholder="Avatar">
          </div>
<!--         Edit Description-->
          <div class="flex flex-col space-y-1">
            <label for="desc">Description</label>
            <textarea id="desc" v-model="description" class="shadow appearance-none border rounded w-full py-2 px-3 text-gray-700 leading-tight focus:outline-none focus:shadow-outline" placeholder="Description"></textarea>
          </div>
          <div class="flex flex-col space-y-1">
            <label for="email">Email</label>
            <input type="email" id="email" v-model="email" class="shadow appearance-none border rounded w-full py-2 px-3 text-gray-700 leading-tight focus:outline-none focus:shadow-outline" placeholder="Your Email">
          </div>

<!--          Edit Date of Birth-->
          <div class="flex flex-col space-y-1">
            <label for="dob">Date of Birth</label>
            <input type="date" id="dob" v-model="birthDate" class="shadow appearance-none border rounded w-full py-2 px-3 text-gray-700 leading-tight focus:outline-none focus:shadow-outline" placeholder="Date of Birth">
          </div>
<!--          Edit Button-->
          <div class="flex flex-col space-y-1">
            <button @click="updateDetails" type="button" class="bg-blue-500 hover:bg-blue-700 text-white font-bold py-2 px-4 rounded focus:outline-none focus:shadow-outline">
              Update
            </button>
          </div>
<!--          <button @click="totalAgeYear" type="button" class="bg-blue-500 hover:bg-blue-700 text-white font-bold py-2 px-4 rounded focus:outline-none focus:shadow-outline">-->
<!--            Total Age-->
<!--          </button>-->
        </div>
      </form>

    </div>
  </section>
</div>

</template>

<style scoped>

</style>