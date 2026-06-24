<template>
  <div class="row mt-4">
    <div class="col-md-3">
      <div class="card text-center">
        <div class="card-body">
          <h5>Total Employees</h5>
          <h2>{{ employees.length }}</h2>
        </div>
      </div>
    </div>

    <div class="col-md-3">
      <div class="card text-center">
        <div class="card-body">
          <h5>Present Today</h5>
          <h2>{{ presentCount }}</h2>
        </div>
      </div>
    </div>

    <div class="col-md-3">
      <div class="card text-center">
        <div class="card-body">
          <h5>Monthly Payroll</h5>
          <h2>R{{ payroll }}</h2>
        </div>
      </div>
    </div>

    <div class="col-md-3">
      <div class="card text-center">
        <div class="card-body">
          <h5>Leave Requests</h5>
          <h2>3</h2>
        </div>
      </div>
    </div>
  </div>
</template>

<script setup>
import employees from "../data/employees";

const presentCount = employees.filter((e) => e.attendance === "Present").length;

const payroll = employees.reduce((sum, emp) => sum + emp.salary, 0);
</script>
