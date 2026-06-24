<template>
  <div class="mt-5">
    <h3>Attendance</h3>

    <table class="table table-bordered">
      <thead>
        <tr>
          <th>Name</th>
          <th>Status</th>
        </tr>
      </thead>

      <tbody>
        <tr v-for="employee in employees" :key="employee.id">
          <td>{{ employee.name }}</td>

          <td>
            <select v-model="employee.attendance" class="form-select">
              <option>Present</option>
              <option>Absent</option>
              <option>Remote</option>
            </select>
          </td>
        </tr>
      </tbody>
    </table>
  </div>
</template>

<script setup>
import employees from "../data/employees.js";
</script>
