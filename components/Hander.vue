<template>
  <div class="hander-out-box">
    <div class="header-logo">Azcnr Animation</div>
    <ul class="header-option">
      <NuxtLink to="/cssList">
        <li class="header-item">CSS动画</li>
      </NuxtLink>
      <li class="header-item">SVG动画</li>
      <li class="header-item">Three.js动画</li>
      <n-button strong secondary circle>
        <template #icon>
          <n-icon size="20">
            <svg xmlns="http://www.w3.org/2000/svg" xmlns:xlink="http://www.w3.org/1999/xlink" viewBox="0 0 1024 1024"><path d="M858.5 763.6a374 374 0 0 0-80.6-119.5a375.63 375.63 0 0 0-119.5-80.6c-.4-.2-.8-.3-1.2-.5C719.5 518 760 444.7 760 362c0-137-111-248-248-248S264 225 264 362c0 82.7 40.5 156 102.8 201.1c-.4.2-.8.3-1.2.5c-44.8 18.9-85 46-119.5 80.6a375.63 375.63 0 0 0-80.6 119.5A371.7 371.7 0 0 0 136 901.8a8 8 0 0 0 8 8.2h60c4.4 0 7.9-3.5 8-7.8c2-77.2 33-149.5 87.8-204.3c56.7-56.7 132-87.9 212.2-87.9s155.5 31.2 212.2 87.9C779 752.7 810 825 812 902.2c.1 4.4 3.6 7.8 8 7.8h60a8 8 0 0 0 8-8.2c-1-47.8-10.9-94.3-29.5-138.2zM512 534c-45.9 0-89.1-17.9-121.6-50.4S340 407.9 340 362c0-45.9 17.9-89.1 50.4-121.6S466.1 190 512 190s89.1 17.9 121.6 50.4S684 316.1 684 362c0 45.9-17.9 89.1-50.4 121.6S557.9 534 512 534z" fill="currentColor"></path></svg>
          </n-icon>
        </template>
      </n-button>

    </ul>
  </div>
</template>
<script setup>
</script>
<style lang="less" scoped>
@import "assets/style/main.less";
.hander-out-box{
  position: relative;
  width: 100%;
  height: 100%;
  display: flex;
  justify-content: space-between;
  align-items: center;
  .header-logo{
    position: relative;
    width: 270px;
    font-size: 26px;
    font-weight: bold;
  }
  .header-option{
    width: 100%;
    display: flex;
    justify-content: right;
    align-items: center;
    list-style-type:none;
    .header-item{
      padding: 0 20px;
      color: @text-color;
      font-weight: 600;
    }
    .header-item:hover{
      color: red;
    }
  }
}
</style>