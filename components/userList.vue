<template>
  <div>
    <button @click="toggleSort()" style="margin-bottom: 16px;">
      Sort: {{ sortOrder === 'asc' ? 'ASC' : 'DESC' }}
    </button>

    <table border="1" cellpadding="10">
      <thead>
        <tr>
          <th>Name</th>
          <th>Email</th>
          <th>Age</th>
          <th>Role</th>
        </tr>
      </thead>
      <tbody>
        <tr v-for="user in sortedUsers" :key="user.id">
          <td>{{ user.name }}</td>
          <td>{{ user.email }}</td>
          <td>{{ user.age }}</td>
          <td>{{ user.role }}</td>
        </tr>
      </tbody>
    </table>
  </div>
</template>

<script>
export default {
  props: {
    users: {
      type: Array,
      required: true
    }
  },
  data() {
    return {
      sortOrder: 'asc'
    }
  },
  computed: {
    sortedUsers() {
      return [...this.users].sort((a, b) => {
        return this.sortOrder === 'asc'
          ? a.age - b.age
          : b.age - a.age
      })
    }
  },
  methods: {
    toggleSort() {
      this.sortOrder = this.sortOrder === 'asc' ? 'desc' : 'asc'
    }
  }
}
</script>