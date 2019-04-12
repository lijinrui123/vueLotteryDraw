<template>
  <div class="hello">
     <vue-lottery-draw
            @lotteryClick="lotteryClick"
            @lotteryDone="lotteryDone"
            :lottery-start="lotteryStart"
            :lottery-prizenum="prizeNum"
            :lottery-prizeno="prizeNo"
            :prize-list="prizeListCom"
            lottery-bg="./static/lotteryprobg.png"
            pointer-bg="./static/pointer.png"
        />
  </div>
</template>

<script>
export default {
  name: 'HelloWorld',
  data () {
    return {
      lotteryStart: 0,
      prizeNo: 1,
      prizeNum: 8,
      prizeList: [
        {
          icon: require('../assets/img/bean_500.png'), // 奖品图片
          rotate: '-22.5deg', // 偏移角度
          name: '1易趣豆' // 奖品名称
        },
        {
          icon: require('../assets/img/bean_five.png'),
          rotate: '-67.5deg',
          name: '2豆'
        },
        {
          icon: require('../assets/img/bean_one.png'),
          rotate: '-113.5deg',
          name: '3易趣豆'
        },
        {
          icon: require('../assets/img/point_five.png'),
          rotate: '-158.5deg',
          name: '4积分'
        },
        {
          icon: require('../assets/img/point_ten.png'),
          rotate: '-203.5deg',
          name: '5积分'
        },
        {
          icon: require('../assets/img/bean_500.png'),
          rotate: '-248.5deg',
          name: '6易趣豆'
        },
        {
          icon: require('../assets/img/give_up.png'),
          count: 0,
          rotate: '-293.5deg',
          name: '7未中奖'
        },
        {
          icon: require('../assets/img/bean_500.png'),
          rotate: '-338.5deg',
          name: '8易趣豆'
        }
      ] // 奖品列表
    }
  },
  methods: {
    lotteryClick () {
      this.lotteryStart = 1
      // let randomNum = 1 + parseInt(Math.random() * this.prizeNum)
      // this.prizeNo = randomNum
      this.prizeNo = 1
    },
    lotteryDone (res) {
      this.lotteryStart = 0
      let index = res.prizeNo - 1
      let obj = this.prizeList[index]
      console.log(obj.name)
    }
  },
  computed: {
    /**
         * 1、把后台返回数组，添加rotate属性（奖品在圆内偏移角度（逆时针所以是负数））组成新数组
         * 2、偏移角度算法
         */
    prizeListCom () {
      let newPrizeList = []
      let _rotate = 180 / this.prizeNum// 夹角一半
      let _pinch = 360 / this.prizeNum // 夹角
      let _prizeList = this.prizeList
      for (let item in _prizeList) {
        let obj = _prizeList[item]
        obj.rotate = (360 - _rotate) - (item * _pinch) + 'deg'
        newPrizeList.push(obj)
      }
      return newPrizeList
    }

  }
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
h1, h2 {
  font-weight: normal;
}
ul {
  list-style-type: none;
  padding: 0;
}
li {
  display: inline-block;
  margin: 0 10px;
}
a {
  color: #42b983;
}
</style>
