<template>
  <div class="home">
    <LeftBar />
    <div class="view">
      <SearchBar @click="modelsListClick" />
      <div class="mainViewICon" v-if="willBeChangeViewResult.COMPONENT == ''">
        <svg
          t="1592126426979"
          class="icon"
          viewBox="0 0 1024 1024"
          version="1.1"
          xmlns="http://www.w3.org/2000/svg"
          p-id="31605"
          width="110"
          height="110"
        >
          <path
            d="M664.25 368.542c10.015 0 19.892 0.733 29.673 1.796-26.649-122.81-159.358-214.078-310.826-214.078-169.353 0-308.086 114.233-308.086 259.274 0 83.708 46.165 152.46 123.282 205.785l-30.809 91.73 107.689-53.455c38.558 7.537 69.46 15.309 107.924 15.309 9.663 0 19.231-0.471 28.753-1.226-6.025-20.366-9.522-41.723-9.522-63.862 0.001-133.181 115.58-241.271 261.922-241.271zM498.629 285.874c23.2 0 38.557 15.12 38.557 38.062 0 22.846-15.357 38.156-38.557 38.156-23.107 0-46.261-15.31-46.261-38.156 0-22.942 23.154-38.062 46.261-38.062zM283.015 362.091c-23.107 0-46.403-15.31-46.403-38.156 0-22.942 23.296-38.062 46.403-38.062 23.082 0 38.463 15.12 38.463 38.062 0 22.847-15.381 38.156-38.463 38.156zM945.447 606.151c0-121.888-123.258-221.237-261.684-221.237-146.578 0-262.015 99.349-262.015 221.237 0 122.065 115.437 221.201 262.015 221.201 30.666 0 61.617-7.609 92.426-15.263l84.514 45.787-23.179-76.171c61.856-45.929 107.925-106.803 107.925-175.554zM598.803 567.994c-15.332 0-30.809-15.097-30.809-30.502 0-15.191 15.475-30.477 30.809-30.477 23.296 0 38.558 15.286 38.558 30.477 0 15.405-15.263 30.502-38.558 30.502zM768.251 567.994c-15.213 0-30.595-15.097-30.595-30.502 0-15.191 15.381-30.477 30.595-30.477 23.107 0 38.558 15.286 38.558 30.477 0 15.405-15.451 30.502-38.558 30.502z"
            p-id="31606"
            fill="#f5f5f5"
          />
        </svg>
      </div>
      <div
        class="view-item"
        v-else
        v-bind:is="willBeChangeViewResult.COMPONENT"
        :viewData="willBeChangeViewResult"
      ></div>
    </div>
  </div>
</template>

<script lang="ts">
import { Vue, Component } from "vue-property-decorator";

import LeftBar from "../childConpents/Home/LeftBar.vue";
import SearchBar from "../childConpents/Home/SearchBar.vue";
import ChatView from "../childConpents/Home/ChatView.vue";

import ChangeViewResult from "../interface/ChangeViewResult";

// 组件列表
const components = {
  LeftBar,
  SearchBar,
  ChatView
};

@Component({
  components
})
export default class Home extends Vue {
  private willBeChangeViewResult: ChangeViewResult = { COMPONENT: "", ID: 0 };

  // 得到子组件传递的消息
  private modelsListClick(result: ChangeViewResult) {
    if (result.ID == 0 && result.COMPONENT.toString().trim() == "") return;
    this.willBeChangeViewResult = result; // 决定切换组件
  }
}
</script>

<style lang="scss" scoped>
.home {
  position: relative;
  height: 100%;
  display: grid;
  grid-template-columns: 70px auto;
}

.view {
  position: relative;
  display: grid;
  grid-template-columns: 260px auto;
}

.mainViewICon {
  position: relative;

  svg {
    position: absolute;
    left: calc(50% - 50px);
    top: calc(50% - 50px);
  }
}
</style>