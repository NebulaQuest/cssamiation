<template>
  <div class="out-box">
    <Content>
      <n-upload
          accept=".svg"
          :max="1"
          :on-finish="handleFinish"
      >
        <n-button>点击上传SVG文件</n-button>
        <div v-if="svgUrl">
          <img :src="svgUrl" alt="Uploaded SVG" />
        </div>
      </n-upload>
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
<style scoped lang="less">

</style>