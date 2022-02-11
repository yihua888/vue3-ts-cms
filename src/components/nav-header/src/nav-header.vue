<template>
    <div class="nav-header">
        <i  
        class="fold-menu" 
        :class="isFold ? 'el-icon-s-fold' : 'el-icon-s-unfold'"
        @click="handleFoldClick"></i>
    </div>
</template>

<script lang="ts">
import { defineComponent, ref } from "vue"
export default defineComponent({
    emits:['foldChange'],
    setup(props,{ emit }){
        const isFold = ref(false)
        const handleFoldClick = () => {
            isFold.value = !isFold.value
            emit('foldChange',isFold.value)
        }
        return {
            isFold,
            handleFoldClick
        }
    }
})
</script>

<style scoped lang="less">
.nav-header {
  display: flex;
  width: 100%;

  .fold-menu {
    font-size: 30px;
    cursor: pointer;
  }

  .content {
    display: flex;
    justify-content: space-between;
    align-items: center;
    flex: 1;
    padding: 0 20px;
  }
}
</style>