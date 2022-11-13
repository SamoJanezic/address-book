<template>
  <header></header>

  <main>
    <displayContacts
      :contactData="contacts"
      @contactDelete="deleteFromContacts"
    />
    <button @click="addToContacts()" class="btn-add">
      <i class="fa fa-plus"></i>
    </button>
  </main>
</template>

<script>
import Contacts from "./components/display-contacts.vue";
import axios from "axios";

export default {
  data() {
    return {
      hello: "hello",
      contacts: [
        {
          name: "Samo",
          surname: "Janežič",
          phone: "031212332",
          effect: false,
          profilePic: "/src/assets/pics/alpaca.png",
        },
        {
          name: "Maja",
          surname: "Janežič",
          phone: "045588436",
          effect: false,
          profilePic: "/src/assets/pics/cat.jpeg",
        },
      ],
    };
  },
  components: {
    displayContacts: Contacts,
  },
  methods: {
    addToContacts() {
      let newContact = {
        name: "Mitja",
        surname: "Kukovec",
        phone: "070665776",
        effect: false,
        profilePic: "/src/assets/pics/dog.jpg",
      };
      this.contacts.push(newContact);
    },
    populate() {
      axios
        .get("https://randomapi.com/api/0d13cd5f5233488ddf538c0c1ff8a3b5")
        .then((response) => {
          console.log(response.data.results[0].contact);
          this.contacts.push(response.data.results[0].contact);
        })
        .catch((e) => console.log(e));
    },
    deleteFromContacts(id) {
      console.log(id);
      this.contacts.splice(id, 1);
    },
  },
  // mounted() {
  //   for (let i = 0; i < 3; i++) {
  //     this.populate();
  //   }
  // },
};
// https://randomapi.com/api/6de6abfedb24f889e0b5f675edc50deb?fmt=raw&sole
</script>

<style scoped>
.main {
  /* background-color: rgba(0, 255, 255, 0.1); */
  height: 100%;

}
.contact {
  margin: auto;
  margin: 50px 100px 50px 100px;
  border: 2px solid green;
  position: relative;
}
.btn-add {
  border: 0.4vmin solid rgb(200, 200, 200);
  border-radius: 100%;
  color: black;
  background-color: transparent;
  height: 8vmin;
  width: 8vmin;
  cursor: pointer;
  margin: 8vmin;
  /* float: left; */
  /* position: absolute; */
}
main {
  /* background-color: green; */
}
</style>
