<template>
  <div ref="viewDoc" class="Content" contenteditable="true">
    Lorem ipsum dolor sit amet consectetur adipisicing elit. Sed laudantium tempore aliquid beatae, in placeat voluptatem velit.
     Reprehenderit voluptatem excepturi ex nesciunt minima quam voluptatum quas deleniti, minus odit ducimus.
    Dolorem quod blanditiis laborum usamus sint magni enim voluptatem. Voluptas quisquam cupiditate optio enim?
  </div>
</template>

<script>
export default {
name: 'Content',
    mounted(){
      this.$emit("viewDoc", this.$refs.viewDoc)
    }
}
</script>

<style lang="scss">
.Content{
  padding: 50px 90px;
  margin: 0 auto;
  max-width: 500px;
    min-height: 1000px;
  outline: none;
  background-color: #e4d5d5;
  font-size: 24px;
}
</style>