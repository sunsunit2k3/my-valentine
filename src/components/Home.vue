<template>
  <div>
    <template v-if="showFirstTemplate">
      <img :src="imageSrc" alt="">
      <h1 class="text-4xl my-4 text-center">{{ question }}</h1>
      <div class="choose">
        <button class="yes" @click="handleYesClick">Yes</button>
        <button class="no" @click="handleNoClick">{{ noButtonText }}</button>
      </div>
    </template>
    <template v-else>
      <img :src="newImageSrc" alt="">
      <h1 class="text-4xl my-4 text-center">{{ newQuestion }}</h1>
    </template>
  </div>
</template>

<style scoped>
.yes {
  background-color: green;
  color: white;
  padding: 10px 20px;
  margin: 10px;
  border-radius: 5px;
}

.no {
  background-color: red;
  color: white;
  padding: 10px 20px;
  margin: 10px;
  border-radius: 5px;
}

.choose {
  display: flex;
  justify-content: center;
}

img {
  width: 300px;
  height: 300px;
}
</style>

<script>
import image2 from"@assets/bear_2.gif";
import image1 from "@assets/bear_1.gif";
export default {
  data() {
    return {
      question: "Will you be my Valentine?",
      newQuestion: "I Love You",
      newImageSrc:image2,
      imageSrc: image1,
      noButtonText: "No",
      listNoButtonText: ["No", "Are You Sure?", "Really sure?", "Are you positive???", 
      "Pookie please", 'Just think about it', "If you say no, I'll be very sad", 
      "I'll be very very sad", "I'll be very very very sad", "I'll be very very very very sad",
      "Ok fine, I'll stop asking...","Just kidding, PLEASE SAY YES","You're breaking my heart ;("],
      noButtonIndex: 0,
      showFirstTemplate: true,
    }
  },
  methods: {
    handleYesClick() {
      this.showFirstTemplate = false;
    },
    handleNoClick() {
      // Replace the "No" button text with a different word when "No" button is clicked
      this.noButtonIndex = (this.noButtonIndex + 1) % this.listNoButtonText.length;
      this.noButtonText = this.listNoButtonText[this.noButtonIndex];
    }
  }
}
</script>
