<template>
  <div>
    <el-menu default-active="2" class="el-menu-vertical-demo">
      <el-submenu index="1">
        <template slot="title">
          <i class="el-icon-location"></i>
          <span>导航一</span>
        </template>
        <el-menu-item-group>
          <el-menu-item
            index="1-1"
            id="1-1"
            @mouseover.native="onMouseover"
            @mouseleave.native="onMouseleave"
            >选项1</el-menu-item
          >
          <el-menu-item
            index="1-2"
            id="1-2"
            @mouseover.native="onMouseover"
            @mouseleave.native="onMouseleave"
            >选项2</el-menu-item
          >
        </el-menu-item-group>
      </el-submenu>
      <el-submenu index="2">
        <template slot="title">
          <i class="el-icon-location"></i>
          <span>导航一</span>
        </template>
        <el-menu-item-group>
          <el-menu-item index="2-1" id="2-1">选项1</el-menu-item>
          <el-menu-item index="2-2" id="2-2">选项2</el-menu-item>
        </el-menu-item-group>
      </el-submenu>
    </el-menu>
    <transition name="fade">
      <mini-menu
        id="mini-menu"
        class="mini-menu"
        v-show="isShow"
        @mouseover.native="onMenuMouseover"
        @mouseleave.native="onMouseleave"
      ></mini-menu>
    </transition>
  </div>
</template>

<script>
  /* eslint-disable */

  import MiniMenu from './MiniMenu.vue'
  export default {
    components: { MiniMenu },
    data() {
      return {
        isShow: false,
      }
    },
    methods: {
      onMouseover(e) {
        console.log(e.target.id)
        const o = document.getElementById(e.target.id)
        const mini = document.getElementById('mini-menu')
        mini.style.top = this.getElementTop(o) + 'px'
        mini.style.left = this.getElementLeft(o) + 200 + 'px'
        this.isShow = true
      },

      onMenuMouseover() {
        this.isShow = true
      },

      onMouseleave() {
        console.log(123123)
        this.isShow = false
      },

      getElementTop(element) {
        let actualTop = element.offsetTop //这是获取元素距父元素顶部的距离
        let current = element.offsetParent //这是获取父元素
        while (current !== null) {
          //当它上面有元素时就继续执行
          actualTop += current.offsetTop //这是获取父元素距它的父元素顶部的距离累加起来
          current = current.offsetParent //继续找父元素
        }
        return actualTop
      },

      getElementLeft(element) {
        let actualLeft = element.offsetLeft
        let current = element.offsetParent
        while (current !== null) {
          actualLeft += current.offsetLeft
          current = current.offsetParent
        }
        return actualLeft
      },
    },
  }
</script>

<style scoped>
  .mini-menu {
    position: absolute;
    top: 0;
    left: 500px;
  }
  .fade-enter-active,
  .fade-leave-active {
    transition: all 0.4s ease;
  }

  .fade-enter-from,
  .fade-leave-to {
    opacity: 0;
  }
</style>
