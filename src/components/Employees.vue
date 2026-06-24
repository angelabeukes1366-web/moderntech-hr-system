<template>
  <div class="mt-5">
    <h3>Employees</h3>

    <input
      v-model="search"
      class="form-control mb-3"
      placeholder="Search Employee"
    />

    <div class="card p-3 mb-4">
      <h5>Add Employee</h5>

      <input
        v-model="newEmployee.name"
        class="form-control mb-2"
        placeholder="Name"
      />

      <input
        v-model="newEmployee.department"
        class="form-control mb-2"
        placeholder="Department"
      />

      <input
        v-model="newEmployee.position"
        class="form-control mb-2"
        placeholder="Position"
      />

      <input
        v-model="newEmployee.salary"
        type="number"
        class="form-control mb-2"
        placeholder="Salary"
      />

      <button class="btn btn-primary" @click="addEmployee">Add Employee</button>
    </div>

    <div class="table-responsive">
      <table class="table table-striped">
        <thead>
          <tr>
            <th>Name</th>
            <th>Department</th>
            <th>Position</th>
            <th>Salary</th>
            <th>Action</th>
          </tr>
        </thead>

        <tbody>
          <tr v-for="employee in filteredEmployees" :key="employee.id">
            <td>{{ employee.name }}</td>
            <td>{{ employee.department }}</td>
            <td>{{ employee.position }}</td>
            <td>R{{ employee.salary }}</td>

            <td>
              <button
                class="btn btn-danger btn-sm"
                @click="deleteEmployee(employee.id)"
              >
                Delete
              </button>
            </td>
          </tr>
        </tbody>
      </table>
    </div>
  </div>
</template>

<script setup>
import { ref, computed } from "vue";
import employeeData from "../data/employees.js";

const employees = ref([...employeeData]);

const search = ref("");

const newEmployee = ref({
  name: "",
  department: "",
  position: "",
  salary: "",
});

const filteredEmployees = computed(() => {
  return employees.value.filter((employee) =>
    employee.name.toLowerCase().includes(search.value.toLowerCase()),
  );
});

function addEmployee() {
  if (
    !newEmployee.value.name ||
    !newEmployee.value.department ||
    !newEmployee.value.position ||
    !newEmployee.value.salary
  ) {
    alert("Please complete all fields");
    return;
  }

  employees.value.push({
    id: Date.now(),
    ...newEmployee.value,
  });

  newEmployee.value = {
    name: "",
    department: "",
    position: "",
    salary: "",
  };
}

function deleteEmployee(id) {
  employees.value = employees.value.filter((emp) => emp.id !== id);
}
</script>
