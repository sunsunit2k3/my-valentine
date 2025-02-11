<template>
  <div>
    <template v-if="showFirstTemplate">
      <img :src="imageSrc" alt="">
      <h1 class="text-4xl my-4 text-center">{{ question }}</h1>
      <div class="flex flex-wrap flex-col md:flex-row gap-4 items-center justify-center">
        <button class="bg-green-500 hover:bg-green-700 text-white font-bold py-2 px-4 rounded" @click="handleYesClick"
          :style="{ 'font-size': yesFontSize }">Có</button>
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
      question: "Will you be my girlfriend?",
      newQuestion: "I Love You, Quỳnh Anh :))))",
      newImageSrc: image2,
      imageSrc: image1,
      noButtonText: "Không",
      listNoButtonText: [
    "Không",  
    "Bạn có chắc không?",  
    "Thật sự chắc chắn chứ?",  
    "Bạn có chắc chắn tuyệt đối không???",  
    "Pookie làm ơn đi",  
    "Chỉ cần suy nghĩ lại thôi mà",  
    "Nếu bạn nói không, tôi sẽ rất buồn",  
    "Tôi sẽ rất, rất buồn",  
    "Tôi sẽ rất, rất, rất buồn",  
    "Tôi sẽ rất, rất, rất, rất buồn",  
    "Được rồi, tôi sẽ không hỏi nữa...",  
    "Đùa thôi, LÀM ƠN NÓI CÓ ĐI",  
    "Bạn đang làm trái tim tôi tan vỡ ;("
],
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
