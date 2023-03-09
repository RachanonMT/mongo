<template lang="">
  <div class="row justify-content-center">
    <div class="col-md-10">
      <h2>{{ (this.$route.query.id) ? "Update Student" : "Create Student" }}</h2>
      <form action="">
        <div class="form-group">
          <label for="name">Name</label>
          <input type="text" class="form-control" v-model="student.name">
        </div>
        <div class="form-group">
          <label for="name">Email</label>
          <input type="text" class="form-control" v-model="student.email">
        </div>
        <div class="form-group">
          <label for="name">Phone</label>
          <input type="text" class="form-control" v-model="student.phone">
        </div>
        <div class="form-group mt-3">
          <button class="btn btn-success col-12" @click="(this.$route.query.id) ? updateData(this.$route.query.id) : onSave()">
            {{(this.$route.query.id) ? "Update" : "Create"}}
          </button>
        </div>
      </form>
    </div>
  </div>
</template>

<script>
import axios from "axios";
export default {
  data() {
    let student = {
      name: "",
      email: "",
      phone: "",
    }
    return {
      student
    }
  },
  created() {
    if (this.$route.query.id) {
      this.getData(this.$route.query.id);
    }
  },
  methods: {
    async onSave() {
      try {
        const res = await axios.post('http://localhost:3000/students/create/', this.student)
      } catch (error) {
        console.log(error);
        window.alert('ERROR');
      }
    },
    async getData(id) {
      try {
        const res = await axios.get(`http://localhost:3000/students/${id}`)
        this.student = res.data;
      } catch (error) {
        console.log(error);
      }
    },
    async updateData(id) {
      try {
        await axios.put(`http://localhost:3000/students/update/${id}`, this.student)
        this.$route.push('/view');
      } catch (error) {
        console.log(error);
      }
    }
  },
}
</script>