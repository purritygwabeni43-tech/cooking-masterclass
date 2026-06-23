<template>
  <div id="app">
    <header class="hero">
      <div>
        <p class="eyebrow">Purrity's Restaurant</p>
        <h1>Explore chef-led workshops and save the ones you love.</h1>
        <p class="subtitle">
          Browse curated cooking classes at Purrity's Restaurant, compare skill levels and pricing,
          and keep a wishlist of the sessions you want to revisit.
        </p>
      </div>

      <div class="summary-card">
        <span class="summary-label">Wishlist</span>
        <strong>{{ wishlist.length }}</strong>
        <p>{{ wishlist.length === 0 ? 'No saved sessions yet.' : 'Sessions saved for later.' }}</p>
      </div>
    </header>

    <main class="catalogue-layout">
      <aside class="wishlist-panel">
        <div class="summary-card">
          <span class="summary-label">Wishlist</span>
          <strong>{{ wishlist.length }}</strong>
          <p>{{ wishlist.length === 0 ? 'No saved sessions yet.' : 'Saved sessions' }}</p>
          <ul class="wishlist-list" v-if="wishlist.length">
            <li v-for="item in wishlist" :key="item.id">{{ item.title }}</li>
          </ul>
        </div>
      </aside>

      <section class="course-grid">
        <CourseCard
          v-for="course in courses"
          :key="course.id"
          :course="course"
          :saved="wishlist.some(item => item.id === course.id)"
          @save="addToWishlist"
        />
      </section>
    </main>
  </div>
</template>

<script>
import CourseCard from './components/icons/CourseCard.vue'

export default {
  name: 'App',
  components: {
    CourseCard,
  },
  data() {
    return {
      courses: [
        {
          id: 1,
          title: 'Italian Pasta Mastery',
          chef: ' Mario',
          price: 50,
          skillLevel: 'Beginner',
          available: true,
          image: 'https://i.ibb.co/tpDPbmM8/fine-restaurant-chef-dish-photography-recipe-32879-1102.avif" alt="fine restaurant chef dish photography recipe 32879 1102',
        },
        {
          id: 2,
          title: 'French Pastry Secrets',
          chef: ' Claire',
          price: 70,
          skillLevel: 'Advanced',
          available: false,
          image: 'https://i.ibb.co/F4d7mGbQ/DSC06410-1280x1876.jpg',
        },
        {
          id: 3,
          title: 'Sushi Rolling Workshop',
          chef: 'Aiko',
          price: 80,
          skillLevel: 'Intermediate',
          available: true,
          image: 'https://images.unsplash.com/photo-1553621042-f6e147245754?auto=format&fit=crop&w=800&q=80',
        },
        {
          id: 4,
          title: 'Plant-Based Comfort Food',
          chef: 'Maya',
          price: 45,
          skillLevel: 'Beginner',
          available: true,
          image: 'https://images.unsplash.com/photo-1504674900247-0877df9cc836?auto=format&fit=crop&w=800&q=80',
        },
        {
          id: 5,
          title: 'Seafood Grill Lab',
          chef: 'Elena',
          price: 95,
          skillLevel: 'Intermediate',
          available: false,
          image: 'https://i.ibb.co/ccXNLp63/Grilled-Seafood-Platter-768x960.jpg',
        },
      ],
      wishlist: [],
    }
  },
  methods: {
    addToWishlist(course) {
      if (!this.wishlist.find(item => item.id === course.id)) {
        this.wishlist.push(course)
      }
    },
  },
}
</script>

<style scoped>
#app {
  max-width: 1200px;
  margin: 0 auto;
  padding: 24px 18px 40px;
}

.hero {
  display: grid;
  gap: 1.5rem;
  padding: 2rem;
  border: 1px solid var(--color-border);
  border-radius: 24px;
  background: var(--color-background-soft);
  margin-bottom: 2rem;
}

.eyebrow {
  text-transform: uppercase;
  letter-spacing: 0.24em;
  font-size: 0.8rem;
  margin-bottom: 0.75rem;
  color: #5c8f74;
}

h1 {
  font-size: clamp(2rem, 4vw, 3.2rem);
  line-height: 1.05;
  margin: 0;
  max-width: 10ch;
}

.subtitle {
  margin-top: 1rem;
  color: rgba(28, 38, 35, 0.8);
  max-width: 40rem;
}

.summary-card {
  display: grid;
  gap: 0.5rem;
  align-content: center;
  padding: 1.25rem 1.5rem;
  border-radius: 20px;
  background: #f9fcf8;
  border: 1px solid rgba(92, 143, 116, 0.16);
}

.summary-label {
  text-transform: uppercase;
  color: #5c8f74;
  font-size: 0.75rem;
  letter-spacing: 0.2em;
}

.catalogue-layout {
  display: grid;
  gap: 2rem;
  grid-template-columns: 280px minmax(0, 1fr);
}

.wishlist-panel {
  position: sticky;
  top: 24px;
  align-self: start;
}

.wishlist-list {
  margin: 1rem 0 0;
  padding: 0;
  list-style: none;
  color: rgba(28, 38, 35, 0.85);
}

.wishlist-list li {
  padding: 0.75rem 0;
  border-bottom: 1px solid rgba(92, 143, 116, 0.12);
}

.course-grid {
  display: grid;
  gap: 1.5rem;
  grid-template-columns: repeat(2, minmax(240px, 1fr));
}

@media (max-width: 980px) {
  .catalogue-layout {
    grid-template-columns: 1fr;
  }
}

@media (max-width: 680px) {
  .course-grid {
    grid-template-columns: 1fr;
  }
}
</style>
