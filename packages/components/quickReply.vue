<template>
  <div class="lemon__quick-reply">
    <div class="scrollView scrollView__x scrollView__hasControls">
      <lemon-button class="scrollView__control" @click="handlePrev">
        ◁
      </lemon-button>
      <div class="scrollView__scroller" ref="scrollerRef" @Scroll="onScroll">
        <div class="scrollView__inner">
          <div
            v-for="(item, idx) in data"
            :key="idx"
            class="scrollView__item slide-in-right-item"
          >
            <slot v-bind:item="item">
              <button class="scrollView__reply-btn" type="button" >
                <span> {{ item.name }}</span>
              </button>
            </slot>
          </div>
        </div>
      </div>
      <lemon-button class="scrollView__control" @click="handleNext">
        ▷
      </lemon-button>
    </div>
  </div>
</template>

<script>
export default {
  name: "LemonQuickReply",
  props: {
    // 参考chat ui
    // [{
    //   name:'',
    //   icon:'',
    //   type:'text|event|',
    //   text:'',type=text有效，实质发送的文本
    // }]
    data: {
      type: Array,
      default() {
        return [];
      },
    },
  },
  components: {},
  data() {
    return {};
  },
  created() {},
  mounted() {},
  methods: {
    handlePrev() {
      const el = this.$refs.scrollerRef;
      el.scrollLeft -= el.offsetWidth;
    },

    handleNext() {
      const el = this.$refs.scrollerRef;
      el.scrollLeft += el.offsetWidth;
    },
    onScroll(e) {
      console.log({ e });
    },
  },
};
</script>

<style scoped lang="stylus">
.lemon__quick-reply{
  padding:8px 12px;
}
.scrollView {
  overflow: hidden;
}
.scrollView__control {
  height:28px;
  line-height:1;
  padding: 6px;
  font-size: 1em;
  background:transparent;
  border: none;
  box-shadow: none;
}
.scrollView__control:not(:disabled):hover {
  // color: var(__brand-1);
  background: rgba(0,0,0,.04);
}
.scrollView__scroller {
  scroll-behavior: smooth;
  -webkit-overflow-scrolling: touch;
  -ms-overflow-style: none;
  scrollbar-width: none;
}
.scrollView__scroller::-webkit-scrollbar {
  display: none;
}
.scrollView__fullWidth {
  margin: 0 calc(var(__gutter) * -1);
}
.scrollView__fullWidth:not(.scrollView__hasControls) .scrollView__inner {
  padding: 0 var(__gutter);
}
.scrollView__x .scrollView__scroller {
  display: flex;
  overflow-x: scroll;
  overflow-y: hidden;
  margin-bottom: -18px;
  padding-bottom: 18px;
}
.scrollView__x .scrollView__inner {
  display: flex;
}
.scrollView__x .scrollView__item {
  flex: 0 0 auto;
  margin-left: .5em;
}
.scrollView__x .scrollView__item:first-child {
  margin-left: 0;
}
.scrollView__reply-btn{
  position: relative;
  height:28px;
  line-height: 27px;
  font-size: .9em;
  margin: 0;
  background-color:#fff;
  // border: 1px solid #C5C5C5;
  color:#4B4B4B;
  border: 1px solid transparent;
  border-radius: 15px;
  cursor: pointer;
  transition: .15s ease-in-out;
}
.scrollView__hasControls {
  display: flex;
  align-items: center;
}
.scrollView__hasControls .scrollView__scroller {
  flex: 1;
}
</style>
