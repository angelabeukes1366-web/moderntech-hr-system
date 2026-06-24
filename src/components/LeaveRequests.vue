<template>
  <div class="mt-5">
    <h3>Leave Requests</h3>

    <table class="table table-bordered">
      <thead>
        <tr>
          <th>Employee</th>
          <th>Leave Type</th>
          <th>Days</th>
          <th>Status</th>
          <th>Actions</th>
        </tr>
      </thead>

      <tbody>
        <tr v-for="request in requests" :key="request.id">
          <td>{{ request.employee }}</td>
          <td>{{ request.type }}</td>
          <td>{{ request.days }}</td>
          <td>
            <span
              :class="{
                'text-warning': request.status === 'Pending',
                'text-success': request.status === 'Approved',
                'text-danger': request.status === 'Denied',
              }"
            >
              {{ request.status }}
            </span>
          </td>

          <td>
            <button
              class="btn btn-success btn-sm me-2"
              @click="approveRequest(request)"
            >
              Approve
            </button>

            <button class="btn btn-danger btn-sm" @click="denyRequest(request)">
              Deny
            </button>
          </td>
        </tr>
      </tbody>
    </table>
  </div>
</template>

<script setup>
import { ref } from "vue";

const requests = ref([
  {
    id: 1,
    employee: "John Smith",
    type: "Annual Leave",
    days: 3,
    status: "Pending",
  },
  {
    id: 2,
    employee: "Sarah Adams",
    type: "Sick Leave",
    days: 2,
    status: "Pending",
  },
  {
    id: 3,
    employee: "Emma Wilson",
    type: "Family Responsibility",
    days: 1,
    status: "Pending",
  },
]);

function approveRequest(request) {
  request.status = "Approved";
}

function denyRequest(request) {
  request.status = "Denied";
}
</script>
