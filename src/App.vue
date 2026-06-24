<template>
  <Navbar />

  <div class="container">
    <h1 class="mt-4">ModernTech HR Management System</h1>

    <Dashboard />

    <Employees />

    <Payroll />

    <Attendance />
  </div>
</template>

<script setup>
import Navbar from "./components/Navbar.vue";
import Dashboard from "./components/Dashboard.vue";
import Employees from "./components/Employees.vue";
import Payroll from "./components/Payroll.vue";
import Attendance from "./components/Attendance.vue";
import LeaveRequests from "./components/LeaveRequests.vue";
</script>
