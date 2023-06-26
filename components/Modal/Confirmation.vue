<template>
  <div
    class="fixed inset-0 flex justify-center items-center z-50 bg-opacity-50 bg-black transition ease-in-out delay-150"
  >
    <div class="w-1/2 bg-white text-center py-5 px-8 rounded-xl text">
      <h1 class="text-xl font-semibold">{{ message }}</h1>
      <div class="flex justify-center gap-3 mt-4">
        <Button
          type="button"
          class="bg-gradient-to-br from-gray-500 to-gray-400 px-4 py-2 text-white font-semibold rounded-full"
          content="Cancel"
          @click="$emit('close')"
        />
        <Button
          type="button"
          class="bg-gradient-to-br from-blue-500 to-blue-400 px-4 py-2 text-white font-semibold rounded-full"
          content="Confirm"
          @click="$emit('confirm')"
        />
      </div>
    </div>
  </div>
</template>

<script>
export default {
  props: {
    message: {
      type: String,
      required: true,
    },
  },
};
</script>
