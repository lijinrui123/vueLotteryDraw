# vue-lottery-draw-git
> vue-lottery-draw

> 参考组件 vue-lottery 

> 在基础上扩展奖品图片、名称、数量根据后台数据返回
> 组件样式可配置
## Build Setup
> ES6

```js
npm install vue-lottery-draw --save
import vueLotteryDraw from 'vue-lottery-draw'
Vue.use(vueLotteryDraw)
```

## 调用示例
```
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
```
### props说明

| 参数名 | 参数类型 | 解释 | 是否必传 |
| :--- | :--- | :--- | :--- |
| lottery-prizenum | Number | 奖品总数量 | 是 |
| lottery-prizeno | Number | 从起点开始逆时针算，中奖的是第几个 | 是 |
| lottery-bg | String | 内容区域背景图 | 是 |
| prize-list | String | 奖品数组后台返回的 | 是 |
| pointer-bg | String | 指针背景图 | 是 |
| lottery-class| String | 自定义class | 否 |
| lottery-start | Number | 0为停止，1为开始转动 | 否 |
| lotteryDone | Function | 旋转完成后的回调函数 | 否 |
| lotteryClick | Function | 点击抽奖按钮的回调 | 否 |