<template>
  <div class="wrapper__changefs">
      <div class="box-button__changefs">
        <button @click="showPopup" class="button-fs">
            <img src="https://img.icons8.com/dotty/80/000000/sentence-case.png"/>
        </button>
      </div>
      <div class="btnfs__popup" v-bind:class="{ show: isActive }">
          <button class="btnfs__popup-item" data-el="1"></button>
          <button class="btnfs__popup-item" data-el="6"></button>
          <button class="btnfs__popup-item" data-el="7"></button>
          <button class="btnfs__popup-item" data-el="11"></button>
          <button class="btnfs__popup-item" data-el="13"></button>
          <button class="btnfs__popup-item" data-el="15"></button>
          <button class="btnfs__popup-item" data-el="17"></button>
          <button class="btnfs__popup-item" data-el="19"></button>
          <button class="btnfs__popup-item" data-el="21"></button>
          <button class="btnfs__popup-item" data-el="25"></button>
          <button class="btnfs__popup-item" data-el="30"></button>
          <button class="btnfs__popup-item" data-el="35"></button>
          <button class="btnfs__popup-item" data-el="40"></button>
      </div>
  </div>
</template>

<script>


export default {
name: 'HeaderButtonfs',
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
    
        let btn = document.querySelectorAll('.btnfs__popup-item')
        console.log()
        btn.forEach(el => {
            let numberFs = el.dataset['el'];
            el.innerHTML = numberFs

            el.addEventListener("click", () =>{
              var selection = window.getSelection()
              let selectionString = selection.toString(selection)
              this.isActive = false;
                console.dir(selection)
               if (selectionString.length != 0){
               document.execCommand("fontSize", true, "0");
                const fontElements = selection.anchorNode.parentNode
                fontElements.removeAttribute("size");
                fontElements.style.fontSize = `${numberFs}px`;
               }
            })
        })
    }
}
</script>

<style lang="scss">
.wrapper__changefs{
display: flex;
flex-direction: column;
justify-content: center;
align-items: center;
position: relative;

.box-button__changefs{
    img{
        width: 20px;
        height: 20px;
    }
    .button-fs{
        margin: 20px;
        border-radius: 10px;
        outline: none;
    }
}
    .btnfs__popup{
        position: absolute;
        display: none;
        top: 65px;
        width: 60px;
        background: darkgrey;
        justify-content: space-around;
        align-items: center;
        flex-direction: column;
        outline: none;
    }
    .btnfs__popup-item{
        margin: 2px;
        width: 50px;
        height: 20px;
        text-align: left;
        -webkit-touch-callout: none; /* iOS Safari */
        -webkit-user-select: none;   /* Chrome/Safari/Opera */
        -khtml-user-select: none;    /* Konqueror */
        -moz-user-select: none;      /* Firefox */
        -ms-user-select: none;       /* Internet Explorer/Edge */
        user-select: none;   
    }
    .show{
        display: flex;
    }
}
</style>
