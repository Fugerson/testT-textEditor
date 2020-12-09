<template>
  <div class="Container">
    <header>
      <Header :viewDoc="this.viewDoclink" />
    </header>
    <Content @viewDoc="viewDoc" />
  </div>
</template>

<script>
import Header from './Header/Header.vue'
import Content from './Content/Content.vue'

export default {
name: 'Container',
  components: {
    Header,
    Content
  },
data(){
    return{
        "viewDoclink": {}
          }
      },
    methods: {
      viewDoc(doc){
        this.viewDoclink = doc
      }
    },
}
</script>

<style lang="scss">
.Container{
  max-width: 900px;
  min-height: 1100px;
  margin: 0 auto;
  background: rgb(159, 216, 216);
}
</style>