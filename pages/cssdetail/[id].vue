<template>
  <div class="out-box">
    <Content>
      <div class="center-box">
        <div class="left-box" ref="animatedDiv" v-html="htmlText">
        </div>
        <div class="right-box">
          <div class="right-box-title">样式编辑</div>
          <div class="right-item">
            <div class="item-title">颜色修改：</div>
            <div style="width: 180px">
              <n-color-picker
                  :show-preview="false"
                  :actions="['confirm']"
                  @confirm="handleConfirm"
              />
            </div>
          </div>
          <div class="right-item">
            <div class="item-title">宽度：</div>
            <div>
              <n-input-number v-model:value="styleWidth" placeholder="请输入宽度">
                <template #suffix>
                  px
                </template>
              </n-input-number>
            </div>
          </div>
          <div class="right-item">
            <div class="item-title">最高高度：</div>
            <div>
              <n-input-number v-model:value="styleMaxHeight" placeholder="请输入高度">
                <template #suffix>
                  px
                </template>
              </n-input-number>
            </div>
          </div>
          <div class="right-item">
            <div class="item-title">最低高度：</div>
            <div>
              <n-input-number v-model:value="styleMinHeight" placeholder="请输入高度">
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
          <div class="right-item">
            <div class="item-title">线条数量：</div>
            <div>
              <n-input-number v-model:value="htmlNum" placeholder="请输入条数">
                <template #suffix>
                  条
                </template>
              </n-input-number>
            </div>
          </div>
          <div v-html="cssText"></div>
          <div class="item-code">
            <n-code :code="cssText"   language="html" />
          </div>
        </div>
      </div>
    </Content>
  </div>
</template>

<script setup>
const styleWidth = ref(10);
const styleMaxHeight = ref(110);
const styleMinHeight = ref(10);

const styleTime = ref(1);
const htmlNum = ref(3)
const bgcolor = ref('rgba(1,2,1,1)');
const cssItem = ref(`
  .donghua1{
      margin-right: 10px;
    }
    .donghua2{
      animation-delay: -0.16s;
    }
    .donghua3{
      animation-delay: -0.26s; margin-left: 10px;
    }
`)
const cssText = computed(() => {
  return `<style>
    .loaders{
      display: flex;
    }
    .donghua{
      width: ${styleWidth.value}px;
      height: ${styleMaxHeight.value}px;
      background: ${bgcolor.value} ;
      margin: 0 auto;
      animation: myfirst ${styleTime.value}s infinite ease-in-out;
    }
    ${cssItem.value}
    @keyframes myfirst
    {
      0%,
      80%,
      100% {
        height: ${styleMaxHeight.value}px;
        margin-top: -10px;
      }
      40% {
        height: ${styleMinHeight.value}px;
        margin-top: ${(styleMaxHeight.value - styleMinHeight.value) / 2}px;
      }
    }
    @-webkit-keyframes myfirst
    {
      0%,
      80%,
      100% {
        height: ${styleMaxHeight.value}px;
        margin-top: -10px;
      }
      40% {
        height: ${styleMinHeight.value}px;
        margin-top: ${(styleMaxHeight.value - styleMinHeight.value) / 2}px;
      }
    }
    </style>`
})
let htmlText = computed(()=>{
  return `
 <div class="loaders">
  <div class="donghua donghua1"></div>
  <div class="donghua donghua2"></div>
  <div class="donghua donghua3"></div>
 </div>
`
});
watch(htmlNum,(newValue)=>{
  htmlText = `<div class="loaders">`
  for (let i = 1; i <= newValue; i++) {
    htmlText+= ` <div class='donghua donghua${i}'></div>`
  }
  htmlText+=`</div>`;
  cssItem.value = ''
  for (let i = 1; i <=newValue ; i++) {
    cssItem.value += `
    .donghua${i}{
      margin-right: 10px;
       animation-delay: ${(i-1)*-0.16}s;
    }
    `
  }

})


//修改背景颜色
const handleConfirm = (value) => {
  bgcolor.value = value
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
      height: 500px;
      overflow: auto;
      margin-top: 20px;
    }
  }
}

::-webkit-scrollbar {
  display: none;
}
</style>