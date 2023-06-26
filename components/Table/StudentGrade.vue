<template>
  <div class="flex flex-col">
    <div class="overflow-x-auto sm:-mx-6 lg:-mx-8">
      <div class="inline-block min-w-full py-2 sm:px-6 lg:px-8">
        <div class="overflow-hidden">
          <table class="min-w-full border text-center text-sm font-light">
            <thead class="border-b font-medium text-lg">
              <tr>
                <th scope="col" class="border-r py-4">No</th>
                <th scope="col" class="border-r px-6 py-4">NIS</th>
                <th scope="col" class="border-r px-6 py-4">Student Name</th>
                <th scope="col" class="border-r px-6 py-4">Student Grade</th>
                <th scope="col" class="px-6 py-4">Action</th>
              </tr>
            </thead>
            <tbody class="text-lg">
              <tr class="border-b" v-if="data.length === 0">
                <td colspan="5" class="text-center py-3">
                  Student grade data is not available.
                </td>
              </tr>
              <tr
                class="border-b"
                v-else
                v-for="(student, index) in data"
                :key="index"
              >
                <td class="border-r px-6 py-4">{{ index + 1 }}</td>
                <td class="border-r px-6 py-4">{{ student.nis }}</td>
                <td class="border-r px-6 py-4">{{ student.name }}</td>
                <td class="border-r px-6 py-4">{{ student.grade }}</td>
                <td class="flex items-center justify-center gap-3 py-4 px-3">
                  <Button
                    type="button"
                    className="bg-gradient-to-br from-blue-500 to-blue-400 px-4 py-2 text-white font-semibold rounded-full"
                    content="Edit"
                    @click="$emit('editStudentGrade', student)"
                  />
                  <Button
                    type="button"
                    className="bg-gradient-to-br from-red-500 to-red-400 px-4 py-2 text-white font-semibold rounded-full"
                    content="Delete"
                    @click="$emit('deleteStudentGrade', student.id)"
                  />
                </td>
              </tr>
            </tbody>
          </table>
        </div>
      </div>
    </div>
  </div>
</template>

<script>
export default {
  props: {
    data: {
      type: Array,
      required: true,
    },
  },
};
</script>
