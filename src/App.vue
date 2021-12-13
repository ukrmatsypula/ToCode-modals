<template>
  <div id="app">
    <div class="wrapper">
      <div class="wrapper-content">
        <section>
          <div class="container">
            <Modal
              v-show="modalFirst"
              title="First modal"
              @close="modalFirst = !modalFirst"
            >
              <div slot="body">
                <p>Text</p>
                <button>Well done</button>
              </div>
              <div slot="footer">
                <p>Default footer</p>
                <button>Well done</button>
              </div>
            </Modal>

            <button
              @click="modalFirst = !modalFirst"
              class="btn btnPrimary"
              @keydown.esc="modalFirst = !modalFirst"
            >
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
