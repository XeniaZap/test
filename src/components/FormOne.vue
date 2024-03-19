<template>
    <form @submit.prevent="registerUser" v-show="form === 1">
      <div class="mb-3 row">
        <label for="userName" class="form-label">Name</label>
        <div class="col-sm-10">
          <input
            v-model="formReg.userName"
            type="text"
            class="form-control"
            id="userName"
            placeholder="Your name"
            required
          />
        </div>
      </div>
      <div class="mb-3 row">
        <label for="newPassword" class="form-label">New password</label>
        <div class="col-sm-10">
          <input
            v-model="formReg.newPassword"
            type="password"
            class="form-control"
            id="newPassword"
            required
          />
        </div>
      </div>
      <div class="mb-3 row">
        <label for="confirmPassword" class="form-label">Repeat password</label>
        <div class="col-sm-10">
          <input
            v-model="formReg.confirmPassword"
            type="password"
            class="form-control"
            id="confirmPassword"
            required
          />
        </div>
      </div>
      <button class="btn btn-primary" type="submit">OK</button>
      <button
        @click="form = 2"
        type="button"
        class="btn btn-outline-primary"
        style="margin-left: 10px"
      >
        I already have an account
      </button>
    </form>
    <form @submit.prevent="goToApp" v-show="form === 2">
      <div class="mb-3 row">
        <label for="userName" class="form-label">Name</label>
        <div class="col-sm-10">
          <input
            v-model="formLog.userName"
            type="text"
            class="form-control"
            id="userName"
            placeholder="Your name"
            required
          />
        </div>
      </div>
      <div class="mb-3 row">
        <label for="password" class="form-label">Password</label>
        <div class="col-sm-10">
          <input
            v-model="formLog.password"
            type="password"
            class="form-control"
            id="password"
            required
          />
        </div>
      </div>
      <button class="btn btn-primary" type="submit">OK</button>
      <button
        @click="form = 1"
        type="button"
        class="btn btn-outline-primary"
        style="margin-left: 10px"
      >
        I don't have an account
      </button>
    </form>
  </template>
  
  <script>
  export default {
    data() {
      return {
        form: 1,
        formReg: {
          userName: "",
          newPassword: "",
          confirmPassword: "",
        },
        formLog: {
          userName: "",
          password: "",
        },
      };
    },
    methods: {
      registerUser() {
        if (this.formReg.newPassword !== this.formReg.confirmPassword) {
          alert("Passwords do not match!");
          return;
        }
        console.log("registerUser");
        console.log("name", this.formReg.userName);
        console.log("password", this.formReg.newPassword);
        console.log("confirmPassword", this.formReg.confirmPassword);
        // Clear form after registration
        this.formReg.userName = "";
        this.formReg.newPassword = "";
        this.formReg.confirmPassword = "";
        this.$router.push("/todo");
      },
      goToApp() {
        console.log("goToApp");
        // Clear form after login
        this.formLog.userName = "";
        this.formLog.password = "";
        this.$router.push("/todo");
      },
    },
  };
  </script>
  