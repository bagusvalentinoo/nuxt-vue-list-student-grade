<template>
  <div
    class="fixed inset-0 flex justify-center items-center z-50 bg-opacity-50 bg-black transition ease-in-out delay-150"
  >
    <div class="w-1/2 bg-white text-center py-5 px-8 rounded-xl text">
      <div class="flex justify-start mb-5">
        <h1 class="text-2xl font-semibold">Update Student Grade!</h1>
      </div>
      <div class="flex flex-col ml-3 gap-3">
        <form @submit.prevent="updateStudentGrade">
          <div class="flex flex-col gap-1 mt-3">
            <label for="nis" class="text-left font-semibold"> NIS </label>
            <input
              type="text"
              name="nis"
              id="nis"
              class="border border-gray-300 rounded-md px-3 py-2"
              v-model="updatedStudent.nis"
            />
          </div>
          <div class="flex flex-col gap-1 mt-3">
            <label for="name" class="text-left font-semibold"> Name </label>
            <input
              type="text"
              name="name"
              id="name"
              class="border border-gray-300 rounded-md px-3 py-2"
              v-model="updatedStudent.name"
            />
          </div>
          <div class="flex flex-col gap-1 mt-3">
            <label for="grade" class="text-left font-semibold"> Grade </label>
            <input
              type="text"
              name="grade"
              id="grade"
              class="border border-gray-300 rounded-md px-3 py-2"
              v-model="updatedStudent.grade"
            />
          </div>
          <div class="flex justify-end gap-3 mt-5">
            <Button
              type="button"
              className="bg-gradient-to-br from-gray-500 to-gray-400 px-4 py-2 text-white font-semibold rounded-full"
              content="Cancel"
              @click="$emit('closeModal')"
            />
            <Button
              type="submit"
              className="bg-gradient-to-br from-blue-500 to-blue-400 px-4 py-2 text-white font-semibold rounded-full"
              content="Update"
              @click="updateStudentGrade"
            />
          </div>
        </form>
      </div>
    </div>
  </div>
</template>

<script>
export default {
  props: {
    student: {
      type: Object,
      required: true,
    },
  },
  data() {
    return {
      updatedStudent: { ...this.student },
    };
  },
  methods: {
    updateStudentGrade() {
      this.$emit("updateStudentGrade", this.updatedStudent);
    },
  },
};
</script>
