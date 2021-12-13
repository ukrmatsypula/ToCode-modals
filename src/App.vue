<template>
  <div id="app">
    <div class="wrapper">
      <div class="wrapper-content">
        <section>
          <div class="container">
            <Modal
              v-if="modalFirst"
              title="First modal"
              @close="modalFirst = !modalFirst"
            ></Modal>

            <button @click="modalFirst = !modalFirst" class="btn btnPrimary">
              show first modal
            </button>
          </div>
        </section>
      </div>
    </div>
  </div>
</template>

<script>
import Modal from "./components/Modal";

export default {
  name: "App",
  components: {
    Modal,
  },
  data: () => ({
    modalFirst: false,
  }),
};
</script>
