<template>
  <aside id="side-bar">
    <h3>Add a Job</h3>
    <form class="job-form">
      <label for="title">Title</label>
      <input @keyup="writeTitle" v-model="enteredListing.title" type="text" name="title">
      <label for="pay">Compensation</label>
      <input @keyup="writePay" v-model="enteredListing.pay" type="text" name="pay">
      <label for="description">Description</label>
      <textarea @keyup="writeDescription" v-model="enteredListing.description" name="description" rows="6" cols="40"></textarea>
      <input type="submit" name="submit" @click.prevent="submitButton" />
    </form>
  </aside>
</template>

<script>
export default {
  data: function() {
    return {
      enteredListing: {}
    }

  },
  methods: {
    submitButton(event) {
      this.enteredListing.interested = []
      this.$emit('submitWasPushed', {
        theNewListing: this.enteredListing
      })
      this.enteredListing = {}
    },
    writeTitle(event) {
      this.enteredListing.title = event.target.value
    },
    writePay(event) {
      this.enteredListing.pay = event.target.value
    },
    writeDescription(event) {
      this.enteredListing.description = event.target.value
    }

  }
}
</script>
