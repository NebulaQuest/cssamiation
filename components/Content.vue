<template>
  <div class="content-box">
    <div class="content-header">
      <div class="header-content">
        <Hander/>
      </div>
    </div>
    <div class="content-main">
      <div class="content-box">
        <slot></slot>
      </div>
    </div>
  </div>
</template>
<script setup>

</script>
<style lang="less" scoped>
@header-height:70px;
@all-width:1280px;
.content-box{
  position: relative;
  width: 100%;
  height: 100%;
  overflow: hidden;
  .content-header{
    width: 100%;
    height: @header-height;
    border-bottom: 1px solid rgba(0, 0, 0, .08);;
    .header-content{
      position: relative;
      height: 100%;
      width: @all-width;
      margin: 0 auto;
    }
  }
  .content-main{
    width: 100%;
    min-height: calc(~ '100vh - 1px - ' @header-height);
    .content-box{
      position: relative;
      width: @all-width;
      margin: 0 auto;
      padding: 20px 0;
    }
  }
}
</style>