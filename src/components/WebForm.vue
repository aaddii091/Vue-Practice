<template>
  <form @submit.prevent="submitForm">
    <label>Email :</label>
    <input type="email" required v-model="email" />
    <label>Password :</label>
    <input type="password" required v-model="password" />
    <label>Role</label>
    <select v-model="role">
      <option value="Developer">Web Developer</option>
      <option value="Designer">Web Designer</option>
      <option value="other">other</option>
    </select>
    <label> Terms & Condition</label>
    <input type="checkbox" required v-model="term" />
    <label>Skills</label>
    <input type="text" v-model="TempSkill" @keyup="addskill" />
    <div v-for="e in Skill" :key="e">
      <h1 @click="deleteSkill(e)">
        {{ e }}
      </h1>
    </div>
    <button>Submit</button>
  </form>
  <p>Email : {{ email }}</p>
  <p>Password : {{ password }}</p>
  <p>Role : {{ role }}</p>
  <p>Terms Accepted: {{ term }}</p>
</template>

<script>
export default {
  data() {
    return {
      email: "",
      password: "",
      role: "",
      term: false,
      TempSkill: "",
      Skill: [],
    };
  },
  methods: {
    addskill(e) {
      if (e.key === "," && this.TempSkill) {
        if (!this.Skill.includes(this.TempSkill)) {
          this.Skill.push(this.TempSkill);
        }
      }
    },
    deleteSkill(e) {
      console.log("dsyfgsf");
      this.Skill = this.Skill.filter((item) => {
        return e !== item;
      });
    },
    submitForm() {
      console.log("submitted");
    },
  },
};
</script>

<style></style>
