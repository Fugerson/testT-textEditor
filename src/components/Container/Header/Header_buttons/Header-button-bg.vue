<template>
  <div class="wrapper__changebg">
      <div class="box-button__changebg">
        <button @click="showPopup" class="button-bg">
            <img src="https://img.icons8.com/ios/50/000000/snap-background-to-white.png"/>
        </button>
      </div>
      <div class="btnbg__popup" v-bind:class="{ show: isActive }">
          <button class="btnbg__popup-item" data-el="red"></button>
          <button class="btnbg__popup-item" data-el="white"></button>
          <button class="btnbg__popup-item" data-el="black"></button>
          <button class="btnbg__popup-item" data-el="Aqua"></button>
          <button class="btnbg__popup-item" data-el="BlueViolet"></button>
          <button class="btnbg__popup-item" data-el="Blue"></button>
          <button class="btnbg__popup-item" data-el="DarkOrange"></button>
          <button class="btnbg__popup-item" data-el="Gold"></button>
          <button class="btnbg__popup-item" data-el="Violet"></button>
      </div>
  </div>
</template>

<script>
export default {
name: 'HeaderButtonbg',
data(){
    return{
        isActive: false
          }
      },
    methods: {
        showPopup(){
            if(this.isActive){
                this.isActive = false;
            } else {
                this.isActive = true;
            }
        },
    },
    mounted(){
    
        let btn = document.querySelectorAll('.btnbg__popup-item')
        console.log()
        btn.forEach(el => {
            let color = el.dataset['el'];
            el.style.background = color
            el.addEventListener("click", () =>{
            document.execCommand("hiliteColor", false, color);
            this.isActive = false;
            })
        })
    }
}
</script>

<style lang="scss">
.wrapper__changebg{
display: flex;
flex-direction: column;
justify-content: center;
align-items: center;
position: relative;

.box-button__changebg{
    img{
        width: 15px;
        height: 20px;
    }
    .button-bg{
        margin: 20px;
        border-radius: 10px;
        outline: none;
    }
}
    .btnbg__popup{
        position: absolute;
        display: none;
        top: 65px;
        width: 80px;
        background: darkgrey;
        justify-content: space-around;
        align-items: center;
        flex-wrap: wrap;
        outline: none;
    }
    .btnbg__popup-item{
        margin: 2px;
        width: 20px;
        height: 20px;
        background: #000;
    }
    .show{
        display: flex;
    }
}
</style>