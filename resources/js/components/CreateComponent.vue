<template>
  <div>
    <h1>Create a services {{ services.name }} </h1>
    <form @submit.prevent="addPost">
      <div class="row">
        <div class="col-md-6">
          <div class="form-group">
            <label>User ID: {{ services.userid }} </label>
            <input type="number" class="form-control" v-model="services.userid">
          </div>
        </div>
      </div><br />
      <div class="row">
        <div class="col-md-6">
          <div class="form-group">
            <label>Name: {{ services.name }} </label>
            <input type="text" class="form-control" v-model="services.name">
          </div>
        </div>
       </div><br />
        <div class="row">
        <div class="col-md-6">
          <div class="form-group">
            <label>Description: {{ services.descriptions }} </label>
            <textarea class="form-control" v-model="services.descriptions" rows="8"></textarea>
          </div>
        </div>
       </div><br />
        <div class="row">
          <div class="col-md-6">
            <div class="form-group">
              <label>Minimum Price: {{ services.minimumprice }} </label>
              <input type="number" class="form-control selectric" v-model="services.minimumprice">
            </div>
          </div>
        </div><br />
        <div class="row">
          <div class="col-md-6">
            <div class="form-group">
              <label>Status:</label>
              <select class="form-control selectric" v-model="services.status">
                <option>Active</option>
                <option>Non Active</option>
              </select>
            </div>
          </div>
        </div><br />
        <div class="form-group">
          <button class="btn btn-primary">Add</button>
        </div>
    </form>
  </div>
</template>

<script>
    export default {
        data(){
        return {
          services:{},
          message: "",
        }
    },
    methods: {
      addPost(){
        let uri = 'http://localhost/tmbh_jasa/public/api/servicesadd';
        this.axios.post(uri, this.services).then((response) => {
            this.$router.push({name: 'services'});
            this.message = response.data.message;
        });
      }
    }
  }
</script>