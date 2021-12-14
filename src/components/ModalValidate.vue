<template>
  <Modal title="Second modal example" @close="$emit('closeValidateModal')">
    <div slot="body">
      <form @submit.prevent="">
        <div class="form-item" :class="{ errorInput: $v.name.$error }">
          <label for="name">Name</label>
          <p class="error-text" v-if="!$v.name.required">Field is required</p>
          <p class="error-text" v-if="!$v.name.minLength">
            Name must have at least {{ $v.name.$params.minLength.min }} !
          </p>
          <input
            id="name"
            placeholder="name"
            v-model="name"
            :class="{ error: $v.name.$error }"
            @change="$v.name.$touch()"
          />
        </div>

        <div class="form-item" :class="{ errorEmail: $v.email.$error }">
          <label for="email">Email</label>
          <input id="email" placeholder="email" v-model="email" />
        </div>
        <button type="submit">Second well done</button>
      </form>
    </div>
    <div slot="footer">
      <p>
        Lorem ipsum dolor sit, amet consectetur adipisicing elit. Unde rerum
        facilis tempore dolorem quidem praesentium iusto dolores impedit
      </p>
    </div>
  </Modal>
</template>

<script>
import { required, minLength, email } from "vuelidate/lib/validators";

import Modal from "@/components/Modal";
export default {
  name: "ModalValidate",
  components: {
    Modal,
  },
  data: () => ({
    email: "",
    name: "",
  }),
  validations: {
    name: {
      required,
      minLength: minLength(4),
    },
    email: {
      required,
      email,
    },
  },
};
</script>

<style lang="scss">
.error-text {
  margin-bottom: 8px;
  font-size: 14px;
  color: red;
}

.error-text.error-input .error-text {
  display: block;
}

.input.error {
  border-color: red;
}
</style>
