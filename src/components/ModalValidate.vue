<template>
  <Modal title="Second modal example" @close="$emit('closeValidateModal')">
    <div slot="body">
      <form @submit.prevent="submitSecondForm">
        <label for="name">Name</label>
        <input type="text" required id="name" placeholder="name" />

        <label for="email">Email</label>
        <input type="email" id="email" placeholder="email" />

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
import Modal from "@/components/Modal";
export default {
  name: "ModalValidate",
  components: {
    Modal,
  },
};
</script>

<style></style>
