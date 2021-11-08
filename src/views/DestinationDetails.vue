<template>
  <div>
    <GoBack />
    <section class="destination">
      <h1>{{ destination.name }}</h1>
      <div class="destination-details">
        <img
          :src="require(`@/assets/${destination.image}`)"
          :alt="destination.name"
        />
        <div class="description">
          <p>{{ destination.description }}</p>
        </div>
      </div>
    </section>
    <section class="experiences" id="experience">
      <h2>Top Experiences in {{ destination.name }}</h2>
      <div class="cards">
        <div
          v-for="experience in destination.experiences"
          :key="experience.slug"
          class="card"
        >
          <router-link
            :to="{
              name: 'ExperienceDetails',
              params: { experienceSlug: experience.slug },
              hash: '#experience',
            }"
          >
            <img
              :src="require(`@/assets/${experience.image}`)"
              :alt="experience.slug"
          /></router-link>
          <span class="card__text">{{ experience.name }}</span>
        </div>
      </div>
      <router-view :key="$route.path"></router-view>
    </section>
    <h1>This is --------------- {{ slug }}</h1>
  </div>
</template>

<script>
import store from "@/store.js";
import GoBack from "../components/GoBack.vue";
export default {
  props: {
    slug: {
      type: String,
      required: true,
    },
  },
  components: { GoBack },
  data() {
    return {};
  },
  computed: {
    destination() {
      return store.destinations.find(
        (destination) => destination.slug === this.slug
      );
    },
  },
};
</script>

<style scoped>
img {
  max-width: 600px;
  height: auto;
  width: 100%;
  max-height: 400px;
}
.destination-details {
  display: flex;
  justify-content: space-between;
}
p {
  margin: 0 40px;
  font-size: 20px;
  text-align: left;
}
.experiences {
  padding: 40px 0;
}
.cards {
  display: flex;
  justify-content: space-between;
}
.cards img {
  max-width: 300px;
}
.card {
  padding: 0 20px;
  position: relative;
}
.card__text {
  position: absolute;
  top: 50%;
  left: 50%;
  transform: translate(-50%, -50%);
  color: white;
  font-size: 25px;
  font-weight: bold;
  text-decoration: none;
}
</style>