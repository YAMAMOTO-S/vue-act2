<template>
<div class="activityCreateForm">
          <a
            v-if="!isFormDisplayed"
            class="button is-primary is-block is-alt is-large"
            href="#"
            @click="toggleFormDisplay"
          >New Activity</a>
          <div
            v-if="isFormDisplayed"
            class="create-form"
          >
            <h2>Create Activity</h2>
            <form>
              <div class="field">
                <label class="label">Title</label>
                <div class="control">
                  <input
                    v-model="newActivity.title"
                    class="input"
                    type="text"
                    placeholder="Read a Book"
                  >
                </div>
              </div>
              <div class="field">
                <label class="label">Notes</label>
                <div class="control">
                  <textarea
                    v-model="newActivity.notes"
                    class="textarea"
                    placeholder="Write some notes here"
                  />
                </div>
              </div>
                <!-- category -->
              <div class="field">
                <label class="label">Category</label>
                <div class="control">
                  <select class="select" v-model="newActivity.category">
                    <option value="" desabled>Please Select One</option>
                    <option v-for="category in categories" :key="category.id">{{category.text}}</option>
                  </select>
                </div>
              </div>

              <div class="field is-grouped">
                <div class="control">
                  <button
                    class="button is-link"
                    :disabled="!isFormvalid"
                    @click="createActivity"
                  >
                    Create Activity
                  </button>
                </div>
                <div class="control">
                  <button
                    class="button is-text"
                    @click="toggleFormDisplay"
                  >
                    Cancel
                  </button>
                </div>
              </div>
            </form>
          </div>
          </div>
</template>

<script>
export default {
   props: {
      categories: {
         type: Object,
         required: true
      }
   },

   data(){
      return{
         isFormDisplayed: false,
         newActivity: {
            title: '',
            notes: '',
            category: ''
          },
      }
   },
   computed: {
      isFormvalid(){
            return this.newActivity.title && this.newActivity.notes
          },
   },
   methods: {
       toggleFormDisplay () {
            this.isFormDisplayed = !this.isFormDisplayed
          },
          createActivity () {
            console.log(this.newActivity)
          },
   }
}
</script>


<style scoped>

</style>