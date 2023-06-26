<template>
  <header
    class="relative w-full bg-gradient-to-b from-slate-100 to-white border-b-2 border-slate-900 py-5"
  >
    <div class="w-3/4 mx-auto">
      <div class="flex justify-between items-center">
        <NuxtLink to="/" class="text-3xl font-bold text-rose-600"
          >Pesilat</NuxtLink
        >
        <ul class="flex items-center gap-8">
          <li>
            <NuxtLink
              class="text-xl font-semibold py-2 px-4 bg-gradient-to-tr from-rose-500 to-rose-400 rounded-full text-white"
              to="/"
              >Home</NuxtLink
            >
          </li>
          <li>
            <NuxtLink
              class="text-xl font-semibold py-2 px-4 bg-gradient-to-tr from-rose-500 to-rose-400 rounded-full text-white"
              to="/student"
              >Student</NuxtLink
            >
          </li>
        </ul>
      </div>
    </div>
  </header>
</template>