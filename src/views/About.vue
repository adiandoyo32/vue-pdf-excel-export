<template>
  <div class="about">
    <h1>This is an about page</h1>
      <!-- <pdf src="@/assets/document.pdf"></pdf> -->
      <!-- <img src="@/assets/logo.png" alt=""> -->
      <input type="number" v-model.number="page"> /{{numPages}}
    <pdf src="@/assets/document.pdf" 
      :page="page" 
      @num-pages="numPages = $event" 
      style="width:75%"></pdf>
  </div>
</template>

<script>
import pdf from 'vue-pdf'

export default {
  components: {
    pdf
  },
  data() {
    return {
      page: 1,
      numPages: 1,
    }
  }
}
</script>