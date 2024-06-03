<template>
  <div class="out-box">
    <Content>
      <div class="center-box">
        <div class="left-box" ref="animatedDiv" v-html="htmlText">
        </div>
        <div class="right-box">
          <div class="right-box-title">样式编辑</div>
          <div class="right-item">
            <div class="item-title">背景颜色：</div>
            <div style="width: 180px">
              <n-color-picker
                  :show-preview="false"
                  :actions="['confirm']"
                  @confirm="handleConfirm"
              />
            </div>
          </div>
          <div class="right-item">
            <div class="item-title">转动颜色：</div>
            <div style="width: 180px">
              <n-color-picker
                  :show-preview="false"
                  :actions="['confirm']"
                  @confirm="selctColorHandle"
              />
            </div>
          </div>
          <div class="right-item">
            <div class="item-title">宽高：</div>
            <div>
              <n-input-number v-model:value="styleWidth" placeholder="请输入宽度">
                <template #suffix>
                  px
                </template>
              </n-input-number>
            </div>
          </div>
          <div class="right-item">
            <div class="item-title">线条厚度：</div>
            <div>
              <n-input-number v-model:value="borderHight" placeholder="请输入厚度">
                <template #suffix>
                  px
                </template>
              </n-input-number>
            </div>
          </div>
          <div class="right-item">
            <div class="item-title">持续时间：</div>
            <div>
              <n-input-number v-model:value="styleTime" placeholder="请输入时间">
                <template #suffix>
                  s
                </template>
              </n-input-number>
            </div>
          </div>
          <div v-html="cssText"></div>
          <div class="item-code">
            <n-code :code="htmlText" language="vue" />
            <n-code :code="cssText"   language="html" />
          </div>
        </div>
      </div>
    </Content>
  </div>
</template>

<script setup>
const styleWidth = ref(120);
const styleTime = ref(2);
const bgcolor = ref('rgba(243,243,343,1)');
const selectColor = ref('rgba(52,152,219,1)');
const borderHight = ref(16)
const cssItem = ref(`

`)
const cssText = computed(() => {
  return `<style>
       .loader {
      border: ${borderHight.value}px solid ${bgcolor.value};
      /* Light grey */
      border-top: ${borderHight.value}px solid ${selectColor.value};
      /* Blue */
      border-radius: 50%;
      width: ${styleWidth.value}px;
      height: ${styleWidth.value}px;
      animation: spin ${styleTime.value}s linear infinite;
    }
      @keyframes spin {
      0% {
        transform: rotate(0deg);
      }

      100% {
        transform: rotate(360deg);
      }
    }
    </style>`
})
let htmlText = computed(()=>{
  return `
 <div class="loader">
 </div>
`
});


//修改背景颜色
const handleConfirm = (value) => {
  bgcolor.value = value
}
const selctColorHandle = (value) => {
  selectColor.value = value
}


</script>

<style scoped lang="less">
.center-box {
  display: grid;
  grid-template-columns: 2fr 1fr;
  grid-column-gap: 25px;

  .left-box {
    position: relative;
    width: 100%;
    height: 820px;
    border: 1px solid rgb(226, 232, 240);
    border-radius: 20px;
    display: flex;
    justify-content: center;
    align-items: center;


  }

  .right-box {
    padding: 20px;

    .right-box-title {
      font-size: 24px;
      font-weight: bold;
    }

    .right-item {
      display: grid;
      grid-template-columns: 1fr 2fr;
      align-items: center;
      margin-top: 10px;

      .item-title {
        font-size: 16px;
      }



    }
    .item-code {
      height: 450px;
      overflow: auto;
      margin-top: 20px;
    }
  }
}

::-webkit-scrollbar {
  display: none;
}
</style>