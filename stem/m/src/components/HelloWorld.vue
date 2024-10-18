<template>



  <div style="width: 1580px;">
    <div>
      <div class="title-display">
        {{ userTitle }}
      </div>
    </div>
    <div class="custom">
      <div class="zi1">发电所</div>
      <div class="zi2">变电所</div>
      <div class="zi3">变电所</div>
      <div class="zi4">工厂，家</div>

      <div class="new-white-background">
  家庭用电是220V
      </div>

      <div class="zi5">发电所</div>
      <div class="zi6">变电所</div>
      <div class="zi7">变电所</div>
      <div class="zi8">工厂，家</div>

      <div class="white-background"></div>

      <div class="white-background2"></div>

      <!-- 第一行 -->
      <div class="item1">
        {{ value1 }}kV <!-- 数值1：电压值，单位为kV -->
      </div>
      <!-- 数值4：P = V^2 / R，V = 220V，R = value3 -->
<div class="item5">
  {{ (220 * 220 / value3).toFixed(3) }} W
</div>

      <div class="item6">
        <!-- 数值3：电流I，计算公式为 I = P / (V * 1000)，P固定为220,000W -->
        {{ current1.toFixed(6) }}A
      </div>

      <!-- 第三行 -->
      <div class="item2">
        {{ value2 }}kV <!-- 数值2：电压值，单位为kV -->
      </div>
      <!-- 数值4：P = V^2 / R，V = 220V，R = value4 -->
<div class="item7">
  {{ (220 * 220 / value4).toFixed(3) }} W
</div>

      <div class="item8">
        <!-- 数值3：电流I，计算公式为 I = P / (V * 1000)，P固定为220,000W -->
        {{ current2.toFixed(6) }}A
      </div>

      <!-- 第二行 -->
      <div class="item3">
        {{ value3 }}Ω <!-- 电阻值，单位为Ω -->
      </div>
      <div class="item4">
        {{ value4 }}Ω <!-- 电阻值，单位为Ω -->
      </div>
    </div>
    <div style="display: flex; justify-content: space-around; margin-top: 20px">
      <div>送电电压</div>
      <div>送电电阻</div>
    </div>
    <div style="display: flex; justify-content: space-around; margin-top: 20px">
      <div>
        <div style="width:200px;">
          <!-- 数值1：电压滑块，范围22kV到500kV -->
          <el-slider v-model="value1" :min="22" :max="500" :show-tooltip="false" class="custom-slider"></el-slider>
        </div>
        <div style="width:200px;">
          <!-- 数值2：电压滑块，范围22kV到500kV -->
          <el-slider v-model="value2" :min="22" :max="500" :show-tooltip="false" class="custom-slider"></el-slider>
        </div>
      </div>
      <div>
        <div style="width:200px;">
          <!-- 数值3：电阻滑块 -->
          <el-slider v-model="value3" :min="1" :max="500" :show-tooltip="false" class="custom-slider1"></el-slider>
        </div>
        <div style="width:200px;">
          <!-- 数值4：电阻滑块 -->
          <el-slider v-model="value4" :min="1" :max="500" :show-tooltip="false" class="custom-slider1"></el-slider>
        </div>
      </div>
    </div>

    <div>
      <!-- 输入框，用户输入标题 -->
      <div class="with-border"></div>
      <div class="title-display ">
        {{ userTitle1 }}
      </div>
    </div>
  </div>
</template>



<script>
export default {
  name: 'HelloWorld',
  data() {
    return {
      // 数值1和数值2：电压值，单位为kV
      value1: 22,
      value2: 22,
      // 电阻值，单位为Ω
      value3: 1,
      value4: 1,
      // 固定功率P，单位为W
      power: 220000,
      userTitle: '电气系统', // 用户输入的标题
      userTitle1: `
      图示说明与电力传输原理

  这张图是一个简化的电力传输系统，包括电压、电流、电阻和功率的变化。
  图中分别表示发电站、输电线、变电站和家庭用电。
  电压和电流值标示在输电线上，而电阻和功率值则在变电站和家庭用电端给出。
  我们不仅会学习到高压输电的优势，还会理解家用电功率和电阻的关系。这将帮助同学们全面理解电能的传输和使用。

  1.电力传输中的能量损耗
  当电能从发电站传输到远方的家庭或工厂时，需要通过很长的电线进行传输。在这个过程中，电线会对电流产生阻碍，这种阻碍称为“电阻”。就像在跑步时遇到风的阻力一样，电阻会让一部分电能转化为热量，从而造成能量损失。这种能量损失可以用以下公式表示：

  P损耗＝I²×R
  P损耗是功率损耗，表示浪费掉的电能。
  I是电流，表示电在线路中流动的多少。
  R是传输线路的电阻，表示电线对电流的阻碍程度。一般固定不变。

  从公式中可以看出，电流越大，功率损耗就会越大。因为电流的平方和电阻一起决定了损耗的大小，所以减少电流是降低能量损耗的关键。

  2.为什么要使用高压输电？
  为了减少能量损失，电力公司会在电能传输时使用很高的电压。你可以把电压想象成推动电流流动的“驱动力”。通过提高电压，我们可以在传输相同功率的情况下减小电流，进而减少能量损耗。这可以用功率公式来理解：

  P=V×I
  P是传输的总功率，表示电能的大小。
  V是电压，表示推动电流流动的“力量”。
  I是电流。

  根据这个公式，如果我们提高电压V，而传输的功率P不变，那么电流I就会相应减小。这样，根据损耗公式P损耗＝I²×R，电流减小会使能量损耗显著减少。因此，在远距离传输电能时，采用高压输电能够有效减少能量的浪费。


  3.变电站的作用
  在电能从发电站传输到远方后，它会经过变电站来降低电压，以便适合家庭和工厂使用。高压适合远距离传输，因为它能减少损耗；但高压对家庭设备来说太危险，因此需要在变电站将电压降低到安全的水平，例如220V。

  4.家用电功率的计算与电阻的关系
  当电能到达我们的家庭后，供电电压通常固定为220V。
  在这里，我们可以将两个公式结合起来理解电器的功率与电阻和电压的关系。首先，通过功率公式 P=V×I，再结合欧姆定律V=I×R，可以得到以下推导：P=V×I=V×V/R

  这时，我们可以使用以下公式来计算电器的功率：

  P＝V²/R
  P是用电器的功率，表示电器每秒钟使用的电能。
  V是家庭供电的电压（一般为220V）。
  R是电器的电阻，表示它对电流的阻碍程度。

  这个公式告诉我们，电器的功率取决于电压和电阻的关系。在图中，你可以通过调节电阻R来观察家庭用电的功率变化：
  -当电阻R增大时，功率P会减小。这意味着用电器使用的能量减少。
  -当电阻R减小时，功率P会增加，用电器使用更多的电能。
`
       // 用户输入的副标题
    }
  },
  computed: {
    // 计算数值3：电流I = P / (V * 1000)
    current1() {
      return this.power / (this.value1 * 10000);
    },
    current2() {
      return this.power / (this.value2 * 10000);
    }
  },
  props: {
    msg: String
  }
}
</script>




<style scoped>

.title-display {
  font-size: 24px;
  font-weight: bold;
  color: #333;
  white-space: pre-wrap; /* 保留换行符并合并空白字符 */
  text-align: left; /* 将文本左对齐 */
}


.input-title {
  margin-bottom: 20px;
  width: 300px;
}

.title-display {
  font-size: 24px;
  font-weight: bold;
  color: #333;
}
.with-border {
  border-top: 2px solid #ccc;
  padding-top: 20px;
}
.custom {
  position: relative;
  width: 960px;
  height: 480px;
  margin-left: 320px;
  background-image: url(../assets/ezgif-7-80ef89b334.gif);
}
.item1 {
  position: absolute;
  width: 80px;
  height: 50px;
  background-color: #fff;
  top: 32px;
  left: 382px;
  font-size: 20px;
  color: #ff0000;
}

.item2 {
  position: absolute;
  width: 80px;
  height: 50px;
  background-color: #fff;
  top: 267px;
  left: 382px;
  font-size: 20px;
  color: #ff0000;
}

.item3 {
  position: absolute;
  width: 80px;
  height: 50px;
  background-color: #fff;
  top: 65px;
  left: 800px;
  font-size: 20px;
  color: #0303ff;
}
.item4{
  position: absolute;
  width: 80px;
  height: 50px;
  background-color: #fff;
  top: 300px;
  left: 800px;
  font-size: 20px;
  color: #0303ff;
}

.item5{
  position: absolute;
  width: 200px;
  height: 50px;
  background-color: #fff;
  top: 32px;
  left: 770px;
  font-size: 20px;
  color: #ff0000;
}

.item6{
  position: absolute;
  width: 150px;
  height: 50px;
  background-color: #fff;
  top: 32px;
  left: 491px;
  font-size: 20px;
  color: #ff0000;
}
.item7 {
  position: absolute;
  width: 200px;
  height: 50px;
  background-color: #fff;
  top: 267px;
  left: 770px;
  font-size: 20px;
  color: #ff0000;
}
.item8 {
  position: absolute;
  width: 150px;
  height: 50px;
  background-color: #fff;
  top: 267px;
  left: 491px;
  font-size: 20px;
  color: #ff0000;
}

.white-background {
  position: absolute;
  top: 386px;
  left: 448px;
  width: 80px;
  height: 50px;
  background-color: #fff; /* 白色背景 */
}

.white-background2 {
  position: absolute;
  top: 152px;
  left: 448px;
  width: 80px;
  height: 50px;
  background-color: #fff; /* 白色背景 */
}

.new-white-background {
  position: absolute;
  width: 80px;
  height: 50px;
  background-color: #fff;
  top: 20px;
  left: 970px;
  font-size: 20px;
  color: #0303ff;
}

.zi1 {
  position: absolute;
  width: 100px;
  height: 50px;
  background-color: #fff;
  top: 202px;
  left: 37px;
  font-size: 26px;
  color: #cecdce;
}

.zi2 {
  position: absolute;
  width: 100px;
  height: 50px;
  background-color: #fff;
  top: 202px;
  left: 211px;
  font-size: 26px;
  color: #cecdce;
}
.zi3 {
  position: absolute;
  width: 100px;
  height: 50px;
  background-color: #fff;
  top: 202px;
  left: 679px;
  font-size: 26px;
  color: #cecdce;
}
.zi4 {
  position: absolute;
  width: 150px;
  height: 50px;
  background-color: #fff;
  top: 202px;
  left: 808px;
  font-size: 26px;
  color: #cecdce;
}


.zi5 {
  position: absolute;
  width: 100px;
  height: 50px;
  background-color: #fff;
  top: 437px;
  left: 37px;
  font-size: 26px;
  color: #cecdce;
}

.zi6 {
  position: absolute;
  width: 100px;
  height: 50px;
  background-color: #fff;
  top: 437px;
  left: 211px;
  font-size: 26px;
  color: #cecdce;
}
.zi7 {
  position: absolute;
  width: 100px;
  height: 50px;
  background-color: #fff;
  top: 437px;
  left: 679px;
  font-size: 26px;
  color: #cecdce;
}
.zi8 {
  position: absolute;
  width: 150px;
  height: 50px;
  background-color: #fff;
  top: 437px;
  left: 808px;
  font-size: 26px;
  color: #cecdce;
}
/* 自定义滑块按钮颜色 */
:deep(.custom-slider .el-slider__button) {
  background-color: #ff4c4c; /* 改变滑块按钮的颜色 */
  border-color: #ff4c4c;     /* 改变滑块按钮的边框颜色 */
}
:deep(.custom-slider1 .el-slider__button) {
  background-color: #4c4cff; /* 改变滑块按钮的颜色 */
  border-color: #4c4cff;     /* 改变滑块按钮的边框颜色 */
}
/* 自定义滑块轨道颜色 */
:deep(.custom-slider .el-slider__bar) {
  background-color: #dbdbdb;  /* 改变滑块的轨道颜色 */
}
:deep(.custom-slider1 .el-slider__bar) {
  background-color: #dbdbdb;  /* 改变滑块的轨道颜色 */
}
</style>
