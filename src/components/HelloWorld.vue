<template>
  <div id="list-complete-demo" class="demo">
    <button v-on:click="move">move</button>
    <br>
    &nbsp
    <div class="box">
      <transition-group name="list-complete" tag="div" class="content">
        <div class="list-complete-item" v-for="mockItem in mockAwardList" v-bind:key="mockItem">{{ mockItem }}</div>
      </transition-group>
    </div>
  </div>
</template>

<script>

export default {
  data () {
    return {
      mockAwardList: [
        '137xxxx5722用户砸中xxxx',
        '188xxxx1234用户砸中xxxx',
        '180xxxx5482用户砸中xxxx',
        '144xxxx0192用户砸中xxxx',
        '189xxxx2932用户砸中xxxx',
        '182xxxx1029用户砸中xxxx',
        '177xxxx9527用户砸中xxxx',
        '132xxxx7252用户砸中xxxx',
        '135xxxx1832用户砸中xxxx',
        '190xxxx1362用户砸中xxxx'
      ]
    }
  },
  methods: {
    move: function () {
      this.mockAwardList.splice(0, 1)
    }
  },
  mounted: function () {
    this.move()
  },
  watch: {
    mockAwardList: function (val, oldVal) {
      const _self = this
      if (val.length !== 11 && val.length !== 0) {
        setTimeout(_ => {
          _self.move()
        }, 3000)
      } else {
        console.log('play is over')
      }
    }
  }
}
</script>

<style>

  .demo .box {
    margin: auto;
    height: 20px;
    width: 300px;
    outline: 1px dashed #000;
  }
  .demo .box .content {
    display: flex;
    margin: auto;
    height: 20px;
    overflow: hidden;
  }
  .list-complete-item {
    width: 300px;
    height: 100%;
    flex-shrink: 0; /*指定 flex 元素的收缩规则*/
    transition: all 1s;
    display: inline-block;
  }
  .list-complete-enter, .list-complete-leave-to {
    opacity: 0.4;
    transform: translateX(-200px);
  }
  .list-complete-leave-active {
    position: absolute;
  }

</style>