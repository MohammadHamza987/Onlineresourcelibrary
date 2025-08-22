<template>
  <base-dialog
    v-if="InputisInvalid"
    title="Invalid Input"
    @close="confirmError"
  >
    <template v-slot:default>
      <p>Unfortunately, at least one Input value is Invalid</p>
      <p>
        Kindly check all Inputs and make sure they are filled out correctly.
      </p>
    </template>
    <template v-slot:actions>
      <base-button @click="confirmError">Okay</base-button>
    </template>
  </base-dialog>
  <base-card>
    <form @submit.prevent="submitData">
      <div class="form-control">
        <label for="title">Title</label>
        <input id="title" name="title" type="text" ref="titleInput" />
      </div>
      <div class="form-control">
        <label for="description">Description</label>
        <textarea
          id="description"
          name="description"
          rows="4"
          ref="descriptionInput"
        ></textarea>
      </div>
      <div class="form-control">
        <label for="link">Link</label>
        <input id="link" name="link" type="url" ref="linkInput" />
      </div>
      <div>
        <base-button type="submit">Add Resource</base-button>
      </div>
    </form>
  </base-card>
</template>

<script>
export default {
  data() {
    return {
      InputisInvalid: false,
    };
  },
  inject: ["addResource"],
  methods: {
    submitData() {
      const enteredTitle = this.$refs.titleInput.value;
      const enteredDescription = this.$refs.descriptionInput.value;
      const enteredLink = this.$refs.linkInput.value;

      if (
        enteredTitle.trim() === "" ||
        enteredDescription.trim() === "" ||
        enteredLink.trim() === ""
      ) {
        this.InputisInvalid = true;
        return;
      }

      this.addResource(enteredTitle, enteredDescription, enteredLink);
    },
    confirmError() {
      this.InputisInvalid = false;
    },
  },
};
</script>

<style scoped>
.form-control {
  margin-bottom: 2rem;
  position: relative;
}

.form-control label {
  display: block;
  margin-bottom: 0.6rem;
  font-weight: 600;
  color: #ec4899;
  font-size: 1.05rem;
  text-shadow: 0 2px 4px rgba(0, 0, 0, 0.3);
}

.form-control input,
.form-control textarea {
  width: 100%;
  padding: 14px 18px;
  border: 2px solid rgba(236, 72, 153, 0.3);
  border-radius: 12px;
  font-size: 1em;
  background: rgba(13, 17, 23, 0.7);
  backdrop-filter: blur(10px);
  color: #ffffff;
  margin-top: 0.2rem;
  transition: all 0.3s cubic-bezier(0.34, 1.56, 0.64, 1);
  box-shadow: 
    0 4px 15px rgba(0, 0, 0, 0.3),
    inset 0 1px 0 rgba(236, 72, 153, 0.2);
}

.form-control input::placeholder,
.form-control textarea::placeholder {
  color: rgba(236, 72, 153, 0.7);
}

.form-control input:focus,
.form-control textarea:focus {
  border: 2px solid rgba(236, 72, 153, 0.8);
  outline: none;
  background: rgba(13, 17, 23, 0.9);
  transform: translateY(-2px);
  box-shadow: 
    0 8px 25px rgba(219, 39, 119, 0.2),
    inset 0 1px 0 rgba(236, 72, 153, 0.3);
}

form > div:last-child {
  text-align: right;
  margin-top: 2rem;
}

@media (max-width: 768px) {
  .form-control {
    margin-bottom: 1.5rem;
  }
  .form-control label {
    font-size: 1rem;
    margin-bottom: 0.5rem;
  }
  .form-control input,
  .form-control textarea {
    padding: 12px 16px;
    font-size: 16px; /* Prevents zoom on iOS */
    border-radius: 10px;
  }
  form > div:last-child {
    text-align: center;
    margin-top: 1.5rem;
  }
}

@media (max-width: 480px) {
  .form-control {
    margin-bottom: 1.2rem;
  }
  .form-control label {
    font-size: 0.95rem;
  }
  .form-control input,
  .form-control textarea {
    padding: 10px 14px;
    font-size: 16px;
    border-radius: 8px;
  }
  .form-control input:focus,
  .form-control textarea:focus {
    transform: translateY(-1px);
  }
  form > div:last-child {
    margin-top: 1.2rem;
  }
}
</style>
