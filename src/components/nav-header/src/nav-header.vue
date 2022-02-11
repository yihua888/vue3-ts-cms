<template>
    <div class="nav-header">
        <i  
        class="fold-menu" 
        :class="isFold ? 'el-icon-s-fold' : 'el-icon-s-unfold'"
        @click="handleFoldClick"></i>
        <div class="content">
            <breadcrumb />
            <user-info />
        </div>
    </div>
</template>

<script lang="ts">
import { defineComponent, ref } from "vue"
import UserInfo from './user-info.vue'
import Breadcrumb, { IBreadcrumb } from '@/base-ui/breadcrumb'
export default defineComponent({
    emits:['foldChange'],
    components:{
        UserInfo,
        Breadcrumb
    },
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