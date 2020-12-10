<template>
  <div class="wrapper__changToJson">
      <div class="box-button__changeToJson">
        <button @click="changeToJson" class="button-changeToJson">to JSON</button>
      </div>
  </div>
</template>

<script>
export default {
name: 'HeaderButtonToJson',
props: {
    viewDoc: {
        viewDoc:  HTMLDivElement,
        default: {}
    }
},
data(){
    return{
        "jsonObject": [],
          }
      },
    methods: {
    changeToJson(){


      for(let i = 0; i < this.viewDoc.childNodes.length; i++){
      if(i === 0){
        this.jsonObject = []
      }
          let object = {},
          elOuterHtml = this.viewDoc.childNodes[i].outerHTML

        if(this.viewDoc.childNodes[i].nodeName === "#text"){
          object.text = this.viewDoc.childNodes[i].nodeValue
          this.jsonObject.push(object)
        } else {
          object.text = this.viewDoc.childNodes[i].innerText

            //background to JSON
          if(elOuterHtml.includes('background')){
            let a = elOuterHtml.indexOf("background-color: ")
            let b = elOuterHtml.indexOf(";", a)
            object.bg = elOuterHtml.slice(a + 18, b)

          }//font-size to JSON
          if(elOuterHtml.includes('font-size')){
            let a = elOuterHtml.indexOf("font-size: ")
            let b = elOuterHtml.indexOf(";", a)
            object.fontSize = elOuterHtml.slice(a + 11, b)
            
          }//color to JSON
          if(elOuterHtml.includes(' color')){
            let a = elOuterHtml.indexOf('color="')
            object.color = elOuterHtml.slice(a + 7, a + 14) 
          }

        this.jsonObject.push(object)
        }
      }
      this.jsonObject= JSON.stringify(this.jsonObject, null, '\t');

        console.log(this.jsonObject)
    }
  },
  mounted(){
    alert("JSON look at the console");
  }
}
</script>

<style lang="scss">
.wrapper__changToJson{
display: flex;

    .button-changeToJson{
        height: 40px;
        margin: 20px;
    }
}
</style>