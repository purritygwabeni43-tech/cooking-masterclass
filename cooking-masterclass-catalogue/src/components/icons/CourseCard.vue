<template>
  <article class="course-card">
    <div class="course-image">
      <img :src="course.image" :alt="course.title + ' dish'" />
    </div>

    <div class="course-copy">
      <div class="course-heading">
        <h2>{{ course.title }}</h2>
        <span :class="['status-badge', course.available ? 'available' : 'soldout']">
          {{ course.available ? 'Available' : 'Sold Out' }}
        </span>
      </div>

      <p class="meta"><strong>Chef</strong> {{ course.chef }}</p>
      <p class="meta"><strong>Level</strong> {{ course.skillLevel }}</p>
      <p class="price">R{{ course.price }}</p>
    </div>

    <button
      class="save-button"
      :disabled="saved || !course.available"
      @click="$emit('save', course)"
    >
      <span v-if="saved">Saved</span>
      <span v-else-if="!course.available">Unavailable</span>
      <span v-else>Save to Wishlist</span>
    </button>
  </article>
</template>

<script>
export default {
  props: {
    course: {
      type: Object,
      required: true,
    },
    saved: {
      type: Boolean,
      default: false,
    },
  },
}
</script>

<style scoped>
.course-card {
  display: grid;
  grid-template-rows: auto 1fr auto;
  gap: 1rem;
  min-height: 360px;
  padding: 0;
  border-radius: 22px;
  background: white;
  border: 1px solid var(--color-border);
  box-shadow: 0 12px 34px rgba(78, 97, 86, 0.06);
  overflow: hidden;
}

.course-image {
  min-height: 180px;
  overflow: hidden;
}

.course-image img {
  width: 100%;
  height: 100%;
  object-fit: cover;
  display: block;
}

.course-copy {
  padding: 1.5rem;
}

.save-button {
  margin: 0 1.5rem 1.5rem;
}

.course-heading {
  display: flex;
  justify-content: space-between;
  align-items: flex-start;
  gap: 1rem;
}

.course-heading h2 {
  font-size: 1.2rem;
  margin: 0;
}

.status-badge {
  padding: 0.45rem 0.85rem;
  border-radius: 999px;
  font-size: 0.8rem;
  font-weight: 700;
  text-transform: uppercase;
  letter-spacing: 0.08em;
}

.status-badge.available {
  color: #2f855a;
  background: #ecf8ef;
}

.status-badge.soldout {
  color: #b83223;
  background: #fde8e6;
}

.meta {
  margin: 0.65rem 0 0;
  color: rgba(36, 49, 38, 0.8);
}

.price {
  margin-top: 1rem;
  font-size: 1.5rem;
  font-weight: 700;
  color: #153c2d;
}

.save-button {
  border: none;
  border-radius: 999px;
  padding: 0.95rem 1rem;
  font-size: 0.95rem;
  font-weight: 700;
  cursor: pointer;
  background: #2f855a;
  color: white;
  transition: transform 0.2s ease, background-color 0.2s ease;
}

.save-button:hover:not(:disabled) {
  transform: translateY(-1px);
}

.save-button:disabled {
  background: #cbd5d1;
  cursor: not-allowed;
}
</style>
