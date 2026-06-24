<template>
  <div class="mt-5">
    <h3>Payroll</h3>

    <table class="table table-bordered">
      <thead>
        <tr>
          <th>Name</th>
          <th>Monthly Salary</th>
          <th>Annual Salary</th>
          <th>Payslip</th>
        </tr>
      </thead>

      <tbody>
        <tr v-for="employee in employees" :key="employee.id">
          <td>{{ employee.name }}</td>
          <td>R{{ employee.salary }}</td>
          <td>R{{ employee.salary * 12 }}</td>

          <td>
            <button
              class="btn btn-primary btn-sm"
              @click="selectedEmployee = employee"
            >
              Generate Payslip
            </button>
          </td>
        </tr>
      </tbody>
    </table>

    <div v-if="selectedEmployee" class="card mt-4 p-3">
      <h4>Payslip</h4>

      <p>
        <strong>Employee:</strong>
        {{ selectedEmployee.name }}
      </p>

      <p>
        <strong>Department:</strong>
        {{ selectedEmployee.department }}
      </p>

      <p>
        <strong>Position:</strong>
        {{ selectedEmployee.position }}
      </p>

      <p>
        <strong>Monthly Salary:</strong>
        R{{ selectedEmployee.salary }}
      </p>

      <p>
        <strong>Annual Salary:</strong>
        R{{ selectedEmployee.salary * 12 }}
      </p>
    </div>
  </div>
</template>

<script setup>
import { ref } from "vue";
import employees from "../data/employees.js";

const selectedEmployee = ref(null);
</script>
