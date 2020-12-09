<template>
  <div class="Header">
    <HeaderButtonColor />
    <HeaderButtonBg />
    <HeaderButtonFs />
    <HeaderButtonToJson :viewDoc="viewDoc" />
  </div>
</template>

<script>
import HeaderButtonColor from "./Header_buttons/Header-button-color.vue"
import HeaderButtonBg from "./Header_buttons/Header-button-bg.vue"
import HeaderButtonFs from "./Header_buttons/Header-button-fs.vue"
import HeaderButtonToJson from "./Header_buttons/Header-button-toJSON"

export default {
name: 'Header',
  components: {
    HeaderButtonColor,
    HeaderButtonFs,
    HeaderButtonBg,
    HeaderButtonToJson
  },
props:{
    viewDoc: {
        viewDoc:  HTMLDivElement,
        default: {}
    }
  }
}
</script>

<style lang="scss">
.Header{
  display: flex;
  padding-left: 100px;
}
</style>