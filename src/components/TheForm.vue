<template>
  <form @submit.prevent="submitForm">
    <div
      class="form-control"
      :class="{ invalid: userNameValidity === 'invalid' }"
    >
      <label for="user-name">Name</label>
      <input
        id="user-name"
        name="user-name"
        type="text"
        v-model.trim="userName"
        @blur="validateInput"
        placeholder="Enter your name"
      />
      <p v-if="userNameValidity === 'invalid'">Your name is required</p>
    </div>

    <div
      class="form-control"
      :class="{ invalid: userEmailValidity === 'invalid' }"
    >
      <label for="user-email">Email</label>
      <input
        id="user-email"
        name="user-email"
        type="email"
        v-model.trim="userEmail"
        @blur="validateEmailInput"
        placeholder="Email username"
      />
      <p v-if="userEmailValidity === 'invalid'">Your email is required</p>
    </div>

    <div
      class="form-control"
      :class="{ invalid: projectNameValidity === 'invalid' }"
    >
      <label for="project-name">Project Name</label>
      <input
        id="project-name"
        name="project-name"
        type="text"
        v-model.trim="projectName"
        @blur="validateProjectName"
        placeholder="Enter a brief title describing your request"
      />
      <p v-if="projectNameValidity === 'invalid'">Project Name is required</p>
    </div>

    <div
      class="form-control"
      :class="{ invalid: projectBenefitValidity === 'invalid' }"
    >
      <label for="project-benefit">How does this projects benefit SMART?</label>
      <textarea
        id="project-benefit"
        name="project-benefit"
        type="text"
        v-model.trim="projectBenefit"
        @blur="validateProjectBenefit"
        placeholder="What problem is this solving? Is there a cost savings? Potential revenue?"
      />
      <p v-if="projectBenefitValidity === 'invalid'">
        Project Benefit is required
      </p>
    </div>

    <div
      class="form-control"
      :class="{ invalid: projectDescriptionValidity === 'invalid' }"
    >
      <label for="project-description">Project Description</label>
      <textarea
        id="project-description"
        name="project-description"
        type="text"
        v-model.trim="projectDescription"
        @blur="validateProjectDescription"
        placeholder="Enter detailed description"
      />
      <p v-if="projectDescriptionValidity === 'invalid'">
        Project Description is required
      </p>
    </div>

    <div class="form-control">
      <label for="url">Page Url (Example: https://www.smarttech.com/) </label>
      <input
        id="url"
        name="url"
        type="text"
        v-model.trim="pageUrl"
        placeholder="Enter the Page Url (optional)"
      />
    </div>

    <div class="form-control">
      <label for="date">Date required</label>
      <input
        id="date"
        name="date"
        type="date"
        v-model="dateRequired"
        placeholder="Date required (optional)"
      />
    </div>

    <div>
      <button>Submit</button>
    </div>
  </form>
</template>

<script>
export default {
  data() {
    return {
      userName: '',
      userNameValidity: '',
      userEmail: '',
      userEmailValidity: '',
      projectName: '',
      projectNameValidity: '',
      projectDescription: '',
      projectDescriptionValidity: '',
      projectBenefit: '',
      projectBenefitValidity: '',
      pageUrl: '',
      dateRequired: ''
    };
  },
  methods: {
    submitForm() {
      console.log('Username: ' + this.userName);
      console.log(this.userEmail);
      console.log(this.projectName);
      console.log(this.projectBenefit);
      console.log(this.projectDescription);
      console.log(this.pageUrl);
      console.log(this.dateRequired);
      this.userName = '';
      this.userNameValidity = '';
      this.userEmail = '';
      this.userEmailValidity = '';
      this.projectName = '';
      this.projectNameValidity = '';
      this.projectDescription = '';
      this.projectDescriptionValidity = '';
      this.projectBenefit = '';
      this.projectBenefitValidity = '';
      this.projectUrl = '';
      this.dateRequired = '';
    },
    validateInput() {
      if (this.userName === '') {
        this.userNameValidity = 'invalid';
      } else {
        this.userNameValidity = 'valid';
      }
    },
    validateEmailInput() {
      if (this.userEmail === '') {
        this.userEmailValidity = 'invalid';
      } else {
        this.userEmailValidity = 'valid';
      }
    },
    validateProjectName() {
      if (this.projectName === '') {
        this.projectNameValidity = 'invalid';
      } else {
        this.projectNameValidity = 'valid';
      }
    },
    validateProjectDescription() {
      if (this.projectDescription === '') {
        this.projectDescriptionValidity = 'invalid';
      } else {
        this.projectDescriptionValidity = 'valid';
      }
    },
    validateProjectBenefit() {
      if (this.projectBenefit === '') {
        this.projectBenefitValidity = 'invalid';
      } else {
        this.projectBenefitValidity = 'valid';
      }
    }
  }
};
</script>

<style scoped>
form {
  margin: 2rem auto;
  max-width: 40rem;
  border-radius: 12px;
  box-shadow: 0 2px 8px rgba(0, 0, 0, 0.26);
  padding: 2rem;
  background-color: #ffffff;
}

.form-control {
  margin: 0.5rem 0;
}

.form-control.invalid input {
  border-color: tomato;
}

.form-control.invalid textarea {
  border-color: tomato;
}

.form-control.invalid label {
  color: tomato;
}

label {
  font-weight: bold;
}

h2 {
  font-size: 1rem;
  margin: 0.5rem 0;
}

input,
textarea,
select {
  display: block;
  width: 100%;
  font: inherit;
  margin-top: 0.5rem;
}

select {
  width: auto;
}

input[type='checkbox'],
input[type='radio'] {
  display: inline-block;
  width: auto;
  margin-right: 1rem;
}

input[type='checkbox'] + label,
input[type='radio'] + label {
  font-weight: normal;
}

button {
  font: inherit;
  border: 1px solid #0076bb;
  background-color: #0076bb;
  color: white;
  cursor: pointer;
  padding: 0.75rem 2rem;
  margin-top: 1rem;
  border-radius: 30px;
}

button:hover,
button:active {
  border-color: #002350;
  background-color: #002350;
}
</style>
