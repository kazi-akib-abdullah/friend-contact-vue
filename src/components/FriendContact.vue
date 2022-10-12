<template>
  <li>
    <h2>{{ name }} {{ isFavourite ? "(Favourite)" : "" }}</h2>
    <button @click="toggleFavourite">Toggle Favourite</button>
    <button @click="toggleDetails">Show Details</button>
    <ul v-if="detailsAreVisible">
      <li><strong>Phone: </strong>{{ phone }}</li>
      <li><strong>Email: </strong>{{ email }}</li>
    </ul>
    <button @click="$emit('delete', id)">Delete</button>
  </li>
</template>

<script>

export default {
  props: {
    name: {
      type: String,
      required: true,
    },
    phone: {
      type: String,
      required: true,
    },
    email: {
      type: String,
      required: true,
    },
    isFavourite: {
      type: Boolean,
      required: true,
    },
    id: {
      type: String,
      required: true,
    },
  },
  emits: ["toggle-favourite", 'delete'],
  data() {
    return {
      detailsAreVisible: false,
    };
  },
  methods: {
    toggleDetails() {
      this.detailsAreVisible = !this.detailsAreVisible;
    },
    toggleFavourite() {
      this.$emit("toggle-favourite", this.id);
    },
  },
};
</script>