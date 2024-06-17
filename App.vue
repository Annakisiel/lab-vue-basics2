<script setup>
import { ref, computed } from "vue";
import HelloWorld from "./components/HelloWorld.vue";
import Navbar from "./components/Navbar.vue";
import Footer from "./components/Footer.vue";
import TheWelcome from "./components/TheWelcome.vue"; // Add this import if TheWelcome component exists

const name = ref("Anna");
const country = ref("Poland");
const age = ref("29");

// Function that returns a string using reactive variables
const getMessage = () => {
  return `Hello, my name is ${name.value} and I am ${age.value} years old. I come from ${country.value}.`;
};
const computedMessage = computed(() => getMessage());

// Boolean variable
const showMessage = ref(false);
const toggleMessage = () => {
  showMessage.value = !showMessage.value;
};

// List of posts
const posts = ref([
  {
    title: "Post 1",
    description: "This is Post 1 description",
    content: "This is Post 1 content",
  },
  {
    title: "Post 2",
    description: "This is Post 2 description",
    content: "This is Post 2 content",
  },
  {
    title: "Post 3", // Changed title to be unique
    description: "This is Post 3 description",
    content: "This is Post 3 content",
  },
]);
</script>

<template>
  <header>
    <Navbar />
    <img
      alt="Vue logo"
      class="logo"
      src="./assets/logo.svg"
      width="125"
      height="125"
    />
    <div class="wrapper">
      <HelloWorld msg="You did it!" />
    </div>
  </header>

  <main>
    <TheWelcome />
    <div>
      <p>{{ computedMessage }}</p>
      <p>2 + 2 = {{ 2 + 2 }}</p>
      <button @click="toggleMessage">Toggle</button>
      <p v-if="showMessage">
        This message is conditionally rendered - boolean variable
      </p>
      <h2>List of Posts</h2>
    </div>
    <ul>
      <li v-for="post in posts" :key="post.title">
        <h3>{{ post.title }}</h3>
        <p>{{ post.description }}</p>
        <div>{{ post.content }}</div>
      </li>
    </ul>
  </main>
  <Footer />
</template>

<style scoped>
header {
  line-height: 1.5;
}

.logo {
  display: block;
  margin: 0 auto 2rem;
}

@media (min-width: 1024px) {
  header {
    display: flex;
    place-items: center;
    padding-right: calc(var(--section-gap) / 2);
  }

  .logo {
    margin: 0 2rem 0 0;
  }

  header .wrapper {
    display: flex;
    place-items: flex-start;
    flex-wrap: wrap;
  }
}
</style>
