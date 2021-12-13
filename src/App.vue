<template>
  <div id="app">
    <div class="wrapper">
      <div class="wrapper-content">
        <section>
          <div class="container">
            <Modal
              v-show="modalFirst"
              title="First modal"
              @close="modalFirst = false"
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
              @keydown.esc="modalFirst = false"
            >
              show first modal
            </button>

            <Modal
              v-show="modalSecond.show"
              title="Second modal example"
              @close="modalSecond.show = false"
            >
              <div slot="body">
                <form @submit.prevent="submitSecondForm">
                  <label for="name">Name</label>
                  <input
                    type="text"
                    required
                    id="name"
                    placeholder="name"
                    v-model="modalSecond.name"
                  />

                  <label for="email">Email</label>
                  <input
                    type="email"
                    id="email"
                    placeholder="email"
                    v-model="modalSecond.email"
                  />

                  <button type="submit">Second well done</button>
                </form>
              </div>
              <div slot="footer">
                <p>
                  Lorem ipsum dolor sit, amet consectetur adipisicing elit. Unde
                  rerum facilis tempore dolorem quidem praesentium iusto dolores
                  impedit sapiente! Eaque ex minus exercitationem ad dolorem
                  suscipit illum ipsum, esse quo dolorum minima veritatis
                  temporibus provident, laborum cum itaque unde facere quae
                  adipisci cupiditate dignissimos aliquid corporis. Dolorem
                  tempora asperiores inventore rerum quos! Ipsa rem, praesentium
                  est cum, aut maxime adipisci cupiditate porro laudantium
                  repudiandae quam aliquid enim beatae, natus molestiae sequi.
                  Voluptas suscipit, officia, perferendis reprehenderit nostrum
                  asperiores, voluptate provident cum optio facilis numquam
                  similique. Animi dicta dolores praesentium officiis, dolorum
                  non voluptas accusantium doloremque qui magni culpa distinctio
                  nostrum!
                </p>
              </div>
            </Modal>

            <button
              @click="modalSecond.show = !modalFirst"
              class="btn btnPrimary"
              @keydown.esc="modalSecond.show = false"
            >
              show second modal
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
    modalSecond: {
      show: false,
      name: "",
      email: "",
    },
  }),
  methods: {
    submitSecondForm() {
      console.log({
        name: this.modalSecond.name,
        email: this.modalSecond.email,
      });

      document.forms[0].reset();
      this.modalSecond.show = false;
    },
  },
};
</script>
