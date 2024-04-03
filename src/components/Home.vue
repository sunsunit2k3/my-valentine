<template>
  <div>
    <template v-if="showFirstTemplate">
      <img :src="imageSrc" alt="">
      <h1 class="text-4xl my-4 text-center">{{ question }}</h1>
      <div class="flex flex-wrap flex-col md:flex-row gap-4 items-center justify-center">
        <button class="bg-green-500 hover:bg-green-700 text-white font-bold py-2 px-4 rounded" @click="handleYesClick"
          :style="{ 'font-size': yesFontSize }">Yes</button>
        <button class=" bg-red-500 hover:bg-red-700 text-white font-bold py-2 px-4 rounded" @click="handleNoClick">{{
      noButtonText }}</button>
      </div>
    </template>
    <template v-else>
      <img :src="newImageSrc" alt="">
      <h1 class="text-4xl my-4 text-center">{{ newQuestion }}</h1>
    </template>
  </div>
</template>
<style src="@assets/style.css"></style>

<script>
import image2 from "@assets/bear_2.gif";
import image1 from "@assets/bear_1.gif";
export default {
  data() {
    return {
      question: "Will you be my Valentine?",
      newQuestion: "I Love You",
      newImageSrc: image2,
      imageSrc: image1,
      noButtonText: "No",
      listNoButtonText: ["No", "Are You Sure?", "Really sure?", "Are you positive???",
        "Pookie please", 'Just think about it', "If you say no, I'll be very sad",
        "I'll be very very sad", "I'll be very very very sad", "I'll be very very very very sad",
        "Ok fine, I'll stop asking...", "Just kidding, PLEASE SAY YES", "You're breaking my heart ;("],
      noButtonIndex: 0,
      showFirstTemplate: true,
      yesFontSize: "16px",
      x: 16,
    }
  },
  methods: {
    handleYesClick() {
      this.showFirstTemplate = false;
    },
    handleNoClick() {
      this.x = this.x +16;
      this.noButtonIndex = (this.noButtonIndex + 1) % this.listNoButtonText.length;
      this.noButtonText = this.listNoButtonText[this.noButtonIndex];
      this.yesFontSize =  this.x + "px";;
    }
  }
}
</script>
