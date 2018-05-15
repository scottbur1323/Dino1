<template>
  <main>
    <section>
      <h2>Job Listings</h2>
      <ul v-for="listing in fullArray" id="job-listings" :key="listing.title">
        <li>
          <h4>{{ listing.title }}</h4>
          <small>{{ listing.pay }}</small>
          <p>{{ listing.description }}</p>
          <small>{{ listing.interested.length }} dinos are interested in this job</small>
        </li>
      </ul>
    </section>
    <app-job-form @submitWasPushed="updateList"></app-job-form>
  </main>
</template>

<script>
import JobForm from './Job-form.vue'

export default {
  data: function() {
    return {
      fullArray: [{
        "id": 1,
        "title": "Demolitions Manager",
        "description": "Please destroy things for us.",
        "pay": "$50,000 per year",
        "interested": ["T-Rex"]
      }, {
        "id": 2,
        "title": "Tree Trimming Specialist",
        "description": "Responsible for keeping trees and bushes well trimmed and away from structures. Must be able to dispose of trimmings.",
        "pay": "$23.50 per hour",
        "interested": ["Utahraptor", ""]
      }, {
        "id": 3,
        "title": "Dog Walker",
        "description": "Looking for a dog lover to take our furry friends out three times a day.",
        "pay": "$15 per hour",
        "interested": ["Dromiceiomimus"]
      }, {
        "id": 4,
        "title": "Philosopher",
        "description": "An ink sees a colombia as a boxlike composition. We can assume that any instance of a currency can be construed as a charming macaroni. If this was somewhat unclear, barish lyrics show us how himalayans can be fathers. A statement can hardly be considered a backless denim without also being a feeling.",
        "pay": "24% equity",
        "interested": ["T-Rex", "Utahraptor"]
      }],
      newListing: {}
    }
  },
  methods: {
    updateList: function(event) {
      this.fullArray.unshift(event.theNewListing)
    }
  },
  components: {
    appJobForm: JobForm
  }
}
</script>
