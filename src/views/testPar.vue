<template>
    <div>
      <catalog :title-list="titleList">
        <h1 id="heading-1">1</h1>
        <p style="line-height:250px">content</p>
        <h1 id="heading-2">2</h1>
        <p style="line-height:250px">content</p>
        <h1 id="heading-3">3</h1>
        <p style="line-height:250px">content</p>
        <h1 id="heading-4">4</h1>
        <p style="line-height:250px">content</p>
        <h1 id="heading-5">5</h1>
        <p style="line-height:250px">content</p>
        <h1 id="heading-6">6</h1>
        <p style="line-height:250px">content</p>
        <h1 id="heading-7">7</h1>
        <p style="line-height:250px">content</p>
        <h1 id="heading-8">8</h1>
        <p style="line-height:250px">content</p>
        <h1 id="heading-9">9</h1>
        <p style="line-height:250px">content</p>
        <h1 id="heading-10">10</h1>
      </catalog>
    </div>
  </template>
  
  <script>
  import catalog from './catalog.vue';
  export default {
    components: {
      catalog
    },
    data() {
      return {
        titleList: [
          { title: 'heading-1', level: 0 },
          { title: 'heading-2', level: 1 },
          { title: 'heading-3', level: 0 },
          { title: 'heading-4', level: 2 },
          { title: 'heading-5', level: 0 },
          { title: 'heading-6', level: 0 },
          { title: 'heading-7', level: 1 },
          { title: 'heading-8', level: 0 },
          { title: 'heading-9', level: 0 },
          { title: 'heading-10', level: 0 }
        ]
      };
    },
    mounted() {
    },
    methods: {
    }
  };
  </script>
  
  <style lang="less" scoped>
  </style>
  