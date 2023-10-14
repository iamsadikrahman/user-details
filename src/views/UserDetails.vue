<script setup>

</script>

<template>
<div class="min-w-full min-h-screen my-14">
  <h1 class="text-3xl font-bold mb-10 text-center  ">User Details</h1>
  <section class="grid grid-cols-2 gap-8">
<!--    Personal Details-->
    <div class="flex flex-col items-center bg-white rounded shadow  space-y-5 p-14">
      <h2 class="text-2xl font-semibold -mt-8">Personal Details</h2>
      <img class="rounded-full w-56" src="https://images.unsplash.com/photo-1535713875002-d1d0cf377fde?ixlib=rb-4.0.3&ixid=MnwxMjA3fDB8MHxwaG90by1wYWdlfHx8fGVufDB8fHx8&auto=format&fit=crop&w=774&q=80" alt="Avatar">
      <h2 class=" text-2xl font-semibold">John Doe</h2>
      <p class="text-gray-600 text-center">I am a developer and I love to code web applications using Vue.js and Laravel with Tailwind CSS and Vuetify for frontend and Laravel Livewire for backend.</p>

    <!-- Birth Date, Email-->
      <div class="flex gap-8  items-center justify-center">
        <div class="flex flex-col items-center shadow rounded p-5 space-y-3">
          <h2 class=" text-2xl font-semibold">Birth Date</h2>
          <p class=" text-gray-600">01/01/2000</p>
        </div>
        <div class="flex flex-col items-center  shadow rounded p-5 space-y-3">
          <h2 class=" text-2xl font-semibold">Email</h2>
          <p class=" text-gray-600">john@example.com</p>
        </div>
      </div>
    </div>
<!--    Edit Details-->
    <div class="flex flex-col items-center bg-white rounded shadow space-y-5 p-14">
      <h2 class="text-2xl font-semibold -mt-8">Edit Details</h2>
      <form action="">
        <div class="flex flex-col space-y-3">
          <div class="flex flex-col space-y-1">
            <label for="name">Name</label>
            <input type="text" id="name" class="shadow appearance-none border rounded w-full py-2 px-3 text-gray-700 leading-tight focus:outline-none focus:shadow-outline" placeholder="Your Name">
          </div>
<!--          Edit Avatar-->
          <div class="flex flex-col space-y-1">
            <label for="avatar">Profile Picture</label>
            <input type="file" id="avatar" class="shadow appearance-none border rounded w-full py-2 px-3 text-gray-700 leading-tight focus:outline-none focus:shadow-outline" placeholder="Avatar">
          </div>
<!--         Edit Description-->
          <div class="flex flex-col space-y-1">
            <label for="desc">Description</label>
            <textarea id="desc" class="shadow appearance-none border rounded w-full py-2 px-3 text-gray-700 leading-tight focus:outline-none focus:shadow-outline" placeholder="Description"></textarea>
          </div>
          <div class="flex flex-col space-y-1">
            <label for="email">Email</label>
            <input type="email" id="email" class="shadow appearance-none border rounded w-full py-2 px-3 text-gray-700 leading-tight focus:outline-none focus:shadow-outline" placeholder="Your Email">
          </div>

<!--          Edit Date of Birth-->
          <div class="flex flex-col space-y-1">
            <label for="dob">Date of Birth</label>
            <input type="date" id="dob" class="shadow appearance-none border rounded w-full py-2 px-3 text-gray-700 leading-tight focus:outline-none focus:shadow-outline" placeholder="Date of Birth">
          </div>
<!--          Edit Button-->
          <div class="flex flex-col space-y-1">
            <button type="submit" class="bg-blue-500 hover:bg-blue-700 text-white font-bold py-2 px-4 rounded focus:outline-none focus:shadow-outline">
              Edit
            </button>
          </div>
        </div>
      </form>

    </div>
  </section>
</div>

</template>

<style scoped>

</style>