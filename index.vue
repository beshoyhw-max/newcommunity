<!-- 支持 ElementPlus 组件 -->
<template>
    <!-- 不要直接使用 vueDemoContainer 避免冲突 -->
    <div class="vueDemoContainer" ref="vueDemoRef">
      <div>
        <el-icon size="16" color="#f00">
          <Check />
        </el-icon>
        {{ $$_t('btnList') }}
      </div>
      <ul>
        <li v-for="item in list" :key="item">
          <el-button>{{ item }}</el-button>
        </li>
      </ul>
    </div>
  </template>
  
  <!-- 支持使用组件 -->
  <!-- 1、注册全局组件 -->
  <!-- <script>
  import { defineComponent } from 'vue';
  export default defineComponent({
    //  组件名称（须唯一）
    name: 'VueDemo',
    //  固定入参
    type: 'customComponent'
  });
  </script> -->
  
  <!-- 2、使用全局组件 -->
  <!-- 参数说明：
      name - 组件名称（须唯一，必填）
      setCustomData - 自行处理组件入参（非必填）
  -->
  <!--
  <CommonCard
      name="VueDemo"
      :setCustomData="(data) => data"
  />
  -->
  
  <script setup>
  import { onMounted, ref } from 'vue';
  import { ElMessage } from 'element-plus';
  import { Check } from '@element-plus/icons-vue';
  import {
    /**
     * 增加国际化字段
     */
    i18nMerge,
    /**
     * 国际化插件
     */
    i18n,
    /**
     * 国际化方法
     */
    t,
    /**
     * 语言参数
     */
    lang,
    /**
     * 请求方法（用法与 axios 一致）
     */
    request,
    /**
     * 设置版心宽度 - 整个页面只需要使用一次，写在控制全局样式的文件
     * 可接受任何 css 单位：px % vw
     * setCoreWidth('1600px')
     */
    setCoreWidth,
    /**
     * 设置卡片间距 - 整个页面只需要使用一次，写在控制全局样式的文件
     * setCardGap('50px', '20px')
     * 如上面的例子，卡片纵向间距为 50px，横向间距为 20px
     */
    setCardGap,
    /**
     * 通栏框架
     * 将该元素所在的 .singleFrame 设置为与屏幕同宽
     * setFullFrame(dom)
     */
    setFullFrame,
    /**
     * 给框架添加 class
     * 给该元素所在的 .singleFrame 添加 class
     * setFrameClass(dom, 'customFrame')
     */
    setFrameClass,
    /**
     * 给卡片添加 class
     * 给该元素所在的 .singleCard 添加 class
     * setCardClass(dom, 'customCard')
     */
    setCardClass,
    /**
     * 给祖先元素添加 class
     * 给该元素所在的 .singleCard 添加 class
     * setClosetClass(dom, 'customCardMain', 'singCardMain')
     * 如上面的例子，给 .singCardMain 元素增加了 customCardMain 类名
     */
    setClosetClass,
    /**
     * 获取祖先元素
     * getClosest(dom, 'customCardMain')
     */
    getClosest,
    /**
     * 获取随机图片
     * getRandomImageUrl()
     */
    getRandomImageUrl,
    /**
     * 加载 CDN JS 回调
     * loadJs(url = '', callback = () => {})
     * await loadJs(url = '')
     */
    loadJs,
    /**
     * 加载 CDN CSS
     * loadCss(url = '')
     */
    loadCss,
    /**
     * 获取全局 Store 数据
     * getMainStore()
     */
    getMainStore,

  } from 'CustomUtils';
  
  const vueDemoRef = ref();
  
  const languages = {
    zh: {
      btnList: '按钮列表',
      btn1: '按钮1',
      btn2: '按钮2'
    },
    en: {
      btnList: 'Buttons',
      btn1: 'Button_1',
      btn2: 'Button_2'
    }
  };
  
  const $$_t = i18nMerge(languages);
  
  const list = ref([$$_t('btn1'), $$_t('btn2')]);
  
  //  utils 能力展示
  const utilsTest = () => {
    const dom = vueDemoRef.value;
  
    setFrameClass(dom, 'customFrame');
  
    setCardClass(dom, 'customCard');
  
    setClosetClass(dom, 'customCardMain', 'singCardMain');
  
    setFullFrame(dom);
  };
  
  //  需要操作 dom 的方法，需要等到 mounted 之后
  onMounted(() => {
    ElMessage.success('ElMessage OK');
    utilsTest();
  });
  </script>
  
  <!-- 支持 less 写法，但是 style 标签上不要加 lang="less" -->
  <style scoped>
  .vueDemoContainer {
    > ul {
      > li {
        padding: 10px;
      }
    }
  }
  </style>
  