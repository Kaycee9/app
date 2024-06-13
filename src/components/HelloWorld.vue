<template>
  <div>
    <div class="formContainer">
      <img class="myImg" src="../assets/face.png" alt="face image" />
      <form @submit.prevent="btnSubmit" class="myForm">
        <h2 class="signUp">SIGN-UP</h2>

        <label>Email*</label>
        <input type="email" v-model="email" />

        <label>Passward*</label>
        <input type="password" v-model="passward" />

        <button class="signInBtn">sign in</button>
      </form>
    </div>

    <!-- <p>email is: {{ email }}</p>
    <p>password is: {{ passward }}</p> -->
  </div>
</template>

<script>
export default {
  data() {
    return {
      email: "",
      passward: "",
    };
  },
  methods: {
    btnSubmit() {
      if (this.passward.length > 5) {
        alert("submitted");
      } else {
        alert("password too short");
      }
    },
  },
};
</script>

<style>
.formContainer {
  display: flex;
  justify-content: space-around;
  align-items: center;
  margin: 1em;
  gap: none;
}
.myForm {
  width: 35%;
  /* margin-right: auto;
  margin-left: auto;
  margin-bottom: 5em; */
  /* background-color: none; */
  padding: 2em;
}
.myImg {
  width: 35%;
}
.signUp {
  display: block;
}
.myForm label {
  display: inline-block;
  margin: 0.5em;
  padding: 0.5em;
  font-weight: 400;
  color: black;
}
.myForm input {
  display: block;
  margin: 0.5em 8em;
  width: 60%;
  padding: 0.7em 0em;
  background-color: rgba(255, 255, 255, 0);
  border: none;
  border-bottom: 3px solid rgb(2, 2, 119);
  cursor: pointer;
  outline: none;
}
.signInBtn {
  margin: 2em 1em;
  padding: 1em 2.5em;
  font-size: 1em;
  background-color: rgb(2, 2, 119);
  color: white;
  border: 1em;
  cursor: pointer;
  border-radius: 0.5em;
  width: 60%;
}
</style>
