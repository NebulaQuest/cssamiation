<template>
  <div class="out-box">
    <Content>
    </Content>
  </div>
</template>
<script setup>
const svgUrl = ref(null);

const handleFinish = ({ file }) => {
  const reader = new FileReader();
  reader.onload = (e) => {
    svgUrl.value = e.target.result;
  };
  reader.readAsDataURL(file.file);
};
</script>
<style lang="less" scoped>
.out-box{
  position: relative;
  width: 100%;
  height: 100%;
}
</style>