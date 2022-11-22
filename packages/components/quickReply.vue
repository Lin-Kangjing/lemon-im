<template>
  <div
    class="lemon-quick-reply ScrollView ScrollView--x ScrollView--hasControls"
  >
    <lemon-button class="ScrollView-control" @click="handlePrev">
      ＜</lemon-button
    >
    <div class="ScrollView-scroller" ref="scrollerRef" @Scroll="onScroll">
      <div class="ScrollView-inner">
        <div
          v-for="item in 10"
          :key="item"
          class="ScrollView-item slide-in-right-item"
        >
          <button class="Btn" type="button">内容{{ item }}</button>
        </div>
      </div>
    </div>
    <lemon-button class="ScrollView-control" @click="handleNext"
      >＞</lemon-button
    >
  </div>
</template>

<script>
export default {
  name: "LemonQuickReply",
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
.ScrollView {
  overflow: hidden;
}
.ScrollView-scroller {
  scroll-behavior: smooth;
  -webkit-overflow-scrolling: touch;
  -ms-overflow-style: none;
  scrollbar-width: none;
}
.ScrollView-scroller::-webkit-scrollbar {
  display: none;
}
.ScrollView--fullWidth {
  margin: 0 calc(var(--gutter) * -1);
}
.ScrollView--fullWidth:not(.ScrollView--hasControls) .ScrollView-inner {
  padding: 0 var(--gutter);
}
.ScrollView--x .ScrollView-scroller {
  display: flex;
  overflow-x: scroll;
  overflow-y: hidden;
  margin-bottom: -18px;
  padding-bottom: 18px;
}
.ScrollView--x .ScrollView-inner {
  display: flex;
}
.ScrollView--x .ScrollView-item {
  flex: 0 0 auto;
  margin-left: .375rem;
}
.ScrollView--x .ScrollView-item:first-child {
  margin-left: 0;
}
.ScrollView--hasControls {
  display: flex;
  align-items: center;
}
.ScrollView--hasControls .ScrollView-scroller {
  flex: 1;
}
.ScrollView-control {
  padding: 6px;
  color: var(--gray-3);
  font-size: 1rem;
}
.ScrollView-control:not(:disabled):hover {
  color: var(--brand-1);
}
</style>
