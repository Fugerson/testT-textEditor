


<template>
  <div class="wrapper__changeColor">
      <div class="box-button__changeColor">
        <button @click="showPopup" class="button-color">
            <img src="https://img.icons8.com/color/48/000000/text-color.png"/>
        </button>
      </div>
      <div class="btnColor__popup" v-bind:class="{ show: isActive }">
          <button class="btncolor__popup-item" data-el="red"></button>
          <button class="btncolor__popup-item" data-el="white"></button>
          <button class="btncolor__popup-item" data-el="black"></button>
          <button class="btncolor__popup-item" data-el="Aqua"></button>
          <button class="btncolor__popup-item" data-el="BlueViolet"></button>
          <button class="btncolor__popup-item" data-el="Blue"></button>
          <button class="btncolor__popup-item" data-el="DarkOrange"></button>
          <button class="btncolor__popup-item" data-el="Gold"></button>
          <button class="btncolor__popup-item" data-el="Violet"></button>
      </div>
  </div>
</template>

<script>


export default {
name: 'HeaderButtonColor',
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
        }
    },
    mounted(){
        let btn = document.querySelectorAll('.btncolor__popup-item')

        btn.forEach(el => {
            let color = el.dataset['el'];
            el.style.background = color
            el.addEventListener("click", () =>{
            document.execCommand("foreColor", false, color);
            this.isActive = false;
            })
        })
    }
}
</script>

<style lang="scss">
.wrapper__changeColor{
display: flex;
flex-direction: column;
justify-content: center;
align-items: center;
position: relative;

.box-button__changeColor{
    
    img{
        width: 20px;
        height: 20px;
    }

    .button-color{
        margin: 20px;
        border-radius: 10px;
        outline: none;
    }
}
    .btnColor__popup{
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
    .btncolor__popup-item{
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