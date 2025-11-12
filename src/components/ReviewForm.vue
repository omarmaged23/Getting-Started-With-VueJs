<script setup>
import {reactive} from 'vue'

const emit = defineEmits(['review-form'])

const review = reactive({
  name : '',
  review : '',
  rating : null
})

const onSubmit = () => {
  if(review.name === '' || review.review === '' || review.rating === null){
    alert('Please, fillout all the fields to proceed')
    return
  }
  const productReview = {
    name:review.name,
    review:review.review,
    rating:review.rating
  }
  emit('review-form',productReview)
    // Clear fields
    review.name = ''
    review.review = ''
    review.rating = null
}
</script>

<template>
  <form class="review-form" @submit.prevent="onSubmit">
    <h3>Leave a review</h3>
    <label for="name">Name:</label>
    <input id="name" v-model="review.name">

    <label for="review">Review:</label>      
    <textarea id="review" v-model="review.review"></textarea>

    <label for="rating">Rating:</label>
    <select id="rating" v-model.number="review.rating">
      <option>5</option>
      <option>4</option>
      <option>3</option>
      <option>2</option>
      <option>1</option>
    </select>

    <input class="button" type="submit" value="Submit">
  </form>
</template>