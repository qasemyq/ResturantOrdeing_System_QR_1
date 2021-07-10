<template>
  <div class="home">

    <MenuT/>
    <SelectedItems/>
  </div>
</template>

<script>
//
// import Menu from '@/components/Menu.vue'
import MenuT from '@/components/MenuT.vue'
import SelectedItems from '@/components/SelectedItems.vue'

export default {
  components: {
    // Menu,
    MenuT,
    SelectedItems
  }
}


</script>
