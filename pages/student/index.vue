<template>
  <Head>
    <Title>Pesilat | Student</Title>
  </Head>
  <Teleport to="body">
    <ModalFormCreateStudentGrade
      v-if="isModalCreateFormOpen"
      @close="isModalCreateFormOpen = !isModalCreateFormOpen"
      @createNewStudentGrade="onCreateNewStudentGrade"
    />
    <ModalFormEditStudentGrade
      v-if="isModalEditFormOpen"
      @closeModal="isModalEditFormOpen = !isModalEditFormOpen"
      @updateStudentGrade="onUpdateStudentGrade"
      :student="editedStudent"
    />
    <ModalConfirmation
      v-if="isModalConfirmationOpen"
      :message="confirmationMessage"
      @close="isModalConfirmationOpen = false"
      @confirm="performConfirmationAction"
    />
  </Teleport>
  <div class="pt-8">
    <div class="flex items-center justify-between mt-3">
      <h1 class="text-2xl font-semibold">List of Students Grade</h1>
      <h2 class="text-lg font-medium">
        Average Grade: {{ calculateAverageGrade() }}
      </h2>
      <Button
        type="button"
        className="bg-gradient-to-br from-blue-500 to-blue-400 px-4 py-2 text-white font-semibold rounded-full"
        content="Add New Student Grade"
        @click="isModalCreateFormOpen = !isModalCreateFormOpen"
      />
    </div>
    <div class="mt-3">
      <TableStudentGrade
        :data="students"
        @editStudentGrade="onEditStudentGrade"
        @deleteStudentGrade="onDeleteStudentGrade"
      />
    </div>
  </div>
</template>

<script>
export default {
  data() {
    return {
      isModalCreateFormOpen: false,
      isModalEditFormOpen: false,
      isModalConfirmationOpen: false,
      confirmationMessage: "",
      confirmationAction: null,
      students: [
        {
          id: 1,
          nis: "201114935",
          name: "Mark Otto",
          grade: "90",
        },
        {
          id: 2,
          nis: "201114936",
          name: "Jacob Thornton",
          grade: "80",
        },
        {
          id: 3,
          nis: "201114937",
          name: "Larry the Bird",
          grade: "70",
        },
        {
          id: 4,
          nis: "201114938",
          name: "Jaysom Kumala",
          grade: "60",
        },
        {
          id: 5,
          nis: "201114939",
          name: "Ambatukam Kusuma",
          grade: "50",
        },
      ],
      editedStudent: null,
    };
  },
  methods: {
    showConfirmationModal(message, action) {
      this.confirmationMessage = message;
      this.confirmationAction = action;
      this.isModalConfirmationOpen = !this.isModalConfirmationOpen;
    },
    performConfirmationAction() {
      if (typeof this.confirmationAction === "function") {
        this.confirmationAction();
      }
    },
    onCreateNewStudentGrade(newStudentGrade) {
      this.students.push({
        id: this.students.length + 1,
        nis: newStudentGrade.nis,
        name: newStudentGrade.name,
        grade: newStudentGrade.grade,
      });
      this.isModalCreateFormOpen = !this.isModalCreateFormOpen;
    },
    onEditStudentGrade(student) {
      this.editedStudent = { ...student };
      this.isModalEditFormOpen = !this.isModalEditFormOpen;
    },
    onUpdateStudentGrade(updatedStudent) {
      const index = this.students.findIndex(
        (student) => student.id === updatedStudent.id
      );
      if (index !== -1) {
        this.students[index] = updatedStudent;
        this.isModalEditFormOpen = !this.isModalEditFormOpen;
      }
    },
    onDeleteStudentGrade(id) {
      const student = this.students.find((student) => student.id === id);
      if (student) {
        const message = `Are you sure you want to delete the student grade of "${student.name}"?`;
        this.showConfirmationModal(message, () => {
          this.students = this.students.filter((student) => student.id !== id);
          this.isModalConfirmationOpen = !this.isModalConfirmationOpen;
        });
      }
    },
    calculateAverageGrade() {
      const sum = this.students.reduce(
        (total, student) => total + parseInt(student.grade),
        0
      );
      const average = sum / this.students.length;
      return average.toFixed(2);
    },
  },
};
</script>
