<template>
  <div>
      <h1>Services</h1>
        <div class="row">
          <div class="col-md-10"></div>
          <div class="col-md-2">
            <router-link :to="{ name: 'create' }" class="btn btn-primary">Add</router-link>
          </div>
        </div><br />

        <table class="table table-hover">
            <thead>
            <tr>
                <th>Id</th>
                <th>User Id</th>
                <th>Name</th>
                <th>Descriptions</th>
                <th>Minimum Price</th>
                <th>Status</th>
                <th>Action</th>
            </tr>
            </thead>
            <tbody>
                <tr v-for="service in services" :key="service.id">
                    <td>{{ service.id }}</td>
                    <td>{{ service.userid }}</td>
                    <td>{{ service.name }}</td>
                    <td>{{ service.descriptions }}</td>
                    <td>{{ service.minimumprice }}</td>
                    <td>{{ service.status }}</td>
                    <td>{{ service.action }}</td>
                    <td><router-link :to="{name: 'edit', params: { id: service.id }}" class="btn btn-primary">Edit</router-link></td>
                    <td><button class="btn btn-danger" @click.prevent="deletePost(service.id)">Delete</button></td>
                </tr>
            </tbody>
        </table>
  </div>
</template>

<script>
  export default {
      data() {
        return {
          services: [],
          count: "",
        }
      },
      created() {
      let uri = 'http://localhost/tmbh_jasa/public/api/services';
      this.axios.get(uri).then(response => {
        this.services = response.data.services;
        this.count = response.data.count;
      });
    },
  }
</script>