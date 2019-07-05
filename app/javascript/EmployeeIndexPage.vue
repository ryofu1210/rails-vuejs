<template>
  <div id="app">
    <table>
      <tbody>
        <tr>
          <th>ID</th>
          <th>name</th>
          <th>department</th>
          <th>gender</th>
          <th>詳細</th>
          <th>編集</th>
        </tr>
        <tr v-for="e in employees" :key="e.id">
          <!-- <td>{{ e.id }}</td> -->
          <td>{{ e.id }}</td>
          <td>{{ e.name }}</td>
          <td>{{ e.department }}</td>
          <td>{{ e.gender }}</td>
          <td><router-link :to="{ name: 'EmployeeDetailPage', params: { id: e.id } }">詳細</router-link></td>
          <td><router-link :to="{ name: 'EmployeeEditPage', params: {id: e.id} }">編集</router-link></td>
        </tr>
      </tbody>
    </table>
  </div>
</template>

<script>
import axios from 'axios';

export default {
  data: function () {
    return {
      employees: []
    }
  },
  mounted () {
    axios
      .get('/api/v1/employees.json')
      .then(response => (this.employees = response.data))
  }
}
</script>

<style scoped>
p {
  font-size: 2em;
  text-align: center;
}
</style>