<template>
  <main>
    <div
      v-for="(contact, idx) in contactData"
      :key="idx"
      @mouseover="contact.effect = true"
      @mouseleave="contact.effect = false"
    >
      <div :key="contact.name" class="grid" :class="{ shadow: contact.effect }">
        <div class="image-wrapper">
          <img :src="contact.profilePic" alt="image" class="image" />
        </div>
        <div class="name">{{ contact.name }} {{ contact.surname }}</div>
        <!-- <div>{{ contact.surname }}</div> -->
        <div>{{ contact.phone }}</div>
        <div>{{ contact.effect }}</div>
        <div>
          <button
            @click="deleteItem(idx)"
            class="btn-del"
            :class="{ show: contact.effect }"
          >
            <i class="fa fa-trash"></i>
          </button>
          <button
            @click="deleteItem(idx)"
            class="btn-del"
            :class="{ show: contact.effect }"
          >
            <i class="fa fa-edit"></i>
          </button>
        </div>
      </div>
    </div>
  </main>
</template>

<script>
export default {
  data() {
    return {};
  },
  props: ["contactData"],
  methods: {
    deleteItem(id) {
      this.$emit("contactDelete", id);
    },
  },
};
</script>

<style scoped>
.grid {
  width: 10%;
  background-color: rgb(245, 255, 255);
  float: left;
  position: relative;
  text-align: center;
  display: inline-grid;
  border: 1px;
  margin: 2% 2%;
  border-color: rgba(223, 225, 229, 0);
  box-shadow: 0 1px 6px 0 rgb(32 33 36 / 28%);
  display: flexbox;
  padding: 15px 40px;
  border-radius: 10px;
  transition: 200ms ease;
}
.name {
  font-size: large;
  font-style: italic;
}
.image {
  margin: 2px 5px;
  object-fit: cover;
  border-radius: 10%;
  height: 100px;
  width: 100px;
  transition: 275ms ease-in-out;
}
.image:hover {
  transform: scale(1.18);
}
.image-wrapper {
  overflow: hidden;
}
.btn-del {
  margin: 10% 14%;
  float: left;
  display: inline;
  border: 0.4vmin solid rgb(200, 200, 200);
  border-radius: 100%;
  color: rgba(0, 0, 0, 0.2);
  background-color: transparent;
  height: 4vmin;
  width: 4vmin;
  cursor: pointer;
  padding-top: 0px;
  padding-right: 16px;
  transition: 250ms ease-in-out;
}
.btn-del:hover {
  color: rgba(0, 0, 0, 0.8);
  border: 0.4vmin solid rgb(167, 27, 27);

}
.shadow {
  transition: 200ms ease;
  border-color: rgba(223, 225, 229, 0);
  box-shadow: 0px 2px 12px 1.5px rgba(10, 128, 155, 0.483);
}
</style>