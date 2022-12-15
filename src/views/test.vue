<template>
    <div style="display: flex;flex-direction: row;">
      <div id="page" class="pageClass" ref="allScrollTop">
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
      </div>
      <div class="menu">
        <div v-for="(item, index) in titleList" :key="index">
          <div :class="'level-' + item.level + '-class'">
            <a
              :href="'#' + item.title"
              :class="
                item.title === activeTitle ? 'activeHrefClass' : 'hrefClass'
              "
            >
              {{ item.title }}
            </a>
          </div>
        </div>
      </div>
    </div>
  </template>
  
  <script>
  export default {
    name: 'AppManage',
    components: {},
    data() {
      return {
        activeTitle: '', // 滚动事件， 当前展示哪条标题
        throttleScroll: null,
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
      this.throttleScroll = this.throttle2(this.onScroll, 200);
      this.activeTitle = this.titleList[0].title;
      window.addEventListener('scroll', this.throttleScroll, true);
    },
    destroy() {
      window.removeEventListener('scroll', this.throttleScroll);
    },
    methods: {
      onScroll() {
        let currScroll = this.$refs.allScrollTop.scrollTop; // 获取滚动条滚了多远
        //   特殊情况 head1
        if (currScroll < this.titleList[0].title) {
          this.activeTitle = this.titleList[0].title;
          return;
        }
        for (let i = 1; i < this.titleList.length; i++) {
          const a = document.getElementById(this.titleList[i - 1].title) // 获取第i-1个title初始高度
            .offsetTop;
          const b = document.getElementById(this.titleList[i].title).offsetTop;
          if (currScroll > a && currScroll < b) {
            this.activeTitle = this.titleList[i].title;
            console.log(this.activeTitle);
            return;
          }
        }
      },
      throttle2(fn, delay) {
        let valid = true;
        return function() {
          if (valid) {
            setTimeout(() => {
              fn.apply(this, arguments);
              valid = true;
            }, delay);
            valid = false;
          }
        };
      }
    }
  };
  </script>
  
  <style lang="less" scoped>
  .pageClass {
    width: 500px;
    height: 600px;
    overflow-y: scroll;
  }
  .level-0-class {
    font-size: 18px;
    margin: 10px;
  }
  .level-1-class {
    font-size: 14px;
    margin-left: 15px;
  }
  .level-2-class {
    font-size: 12px;
    margin-left: 15px;
  }
  .menu {
    width: 150px;
    position: fixed;
    right: 20px;
    display: flex;
    flex-direction: column;
  }
  .hrefClass {
    color: gray;
  }
  .activeHrefClass {
    color: black;
    font-size: 150%;
  }
  </style>
  