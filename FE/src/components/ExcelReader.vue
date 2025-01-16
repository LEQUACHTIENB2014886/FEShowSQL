<template>
  <div>
    <el-row>
      <el-col class="line1" :span="4">
        <div>MODEL NAME</div>
        <div>STYLE NO#</div>
        <div>GANDER</div>
        <div>TECH MEASUREMENTS</div>
        <div>PURPOSE</div>
        <div>LAST NO</div>
        <div>OUTSOLE NO</div>
        <div>VERSION 版本</div>
      </el-col>
      <el-col class="line2" :span="3">
        <div>BONDI 9</div>
        <div>1162011-1162012</div>
        <div>M'S W'S</div>
        <div>( Unit: mm)</div>
        <div>TECH 1</div>
        <div>11920-1</div>
        <div>HOKA-S25-005</div>
        <div></div>
      </el-col>
      <el-col class="line3 image-container" :span="11">
        <img
          src="../assets/shoes/Bondi 9.png"
          alt="Example Image"
          class="image"
        />
      </el-col>
      <el-col class="line4" :span="6">
        <div>跑步鞋 (Running shoes)</div>
        <div>篮球鞋 (Basketball shoes)</div>
        <div>网球鞋 (Tennis shoes)</div>
        <div>步行鞋 (Walking shoes)</div>
      </el-col>
    </el-row>

    <hr />

    <div class="horizontal-row">
      <div class="item">
        <span class="circle">1</span> 头翘高度(BP) Toe Spring(BP)mm
      </div>
      <div class="item">
        <span class="circle">2</span> 鞋頭長度 Vamp length(mm)
      </div>
      <div class="item">
        <span class="circle">3</span> 后跟高度外量 Heel Height(outside)mm
      </div>
      <div class="item">
        <span class="circle">4</span> 后跟高度内量 Heel Height (inside)mm
      </div>
      <div class="item">
        <span class="circle">5</span> 外腰高度内量 Lat collar Height (inside)mm
      </div>
      <div class="item">
        <span class="circle">6</span> 内腰高度内量 Med collar Height(inside)mm
      </div>
      <div class="item">
        <span class="circle">7</span> 鞋舌长度 Tongue Length mm
      </div>
      <div class="item">鞋口开口宽度(从鞋头数来第二排扣子)mm</div>
      <div class="item">鞋口开口宽度(从鞋头数来第四排扣子)mm</div>
      <div class="item">鞋舌 印刷 "HOKA" Logo</div>
      <div class="item">内腰 LOGO"BIRD" MED QUARTER "BIRD" (mm)</div>
      <div class="item">外腰 LOGO"HOKA" LAT QUARTER "HOKA" (mm)</div>
      <div class="item">鞋口飞鸟LOGO“BIRD"印刷</div>
      <div class="item">后套印刷“BONDI 9"LOGO</div>
      <div class="item">入楦长度 On Last Length</div>
      <div class="item">鞋带长度 Lace</div>
      <div class="item">穿到上鞋眼孔鞋帶外露標 (cm)</div>
      <div class="item">产地标 Size Label</div>
      <div class="item">前襯分段 TOE BOX M'S</div>
      <div class="item">鞋撐分段 SHOE INSERT (編號:17561) M'S</div>
      <div class="item">后襯分段 HEEL COUNTER (编号:11920-1) M'S</div>
      <div class="item">內盒 INNER BOX</div>
      <div class="item">包裝紙 WRAPPING PAPER</div>
      <div class="item">Signature</div>
    </div>
  </div>
</template>


<style scoped>
* {
  font-family: "Arial", sans-serif;
  box-sizing: border-box;
}

.el-row {
  display: flex;
  justify-content: space-between;
  gap: 15px;
  background-color: #f7f7f7;
  padding: 15px;
  border-radius: 12px;
}

.line1,
.line2,
.line3,
.line4 {
  padding: 5px;
  font-size: 24px;
  line-height: 1.4;
  background-color: #ffffff;
  border: 2px solid #3498db;
  border-radius: 10px;
  display: flex;
  flex-direction: column;
  gap: 8px;
  flex: 1;
  box-shadow: 0 4px 8px rgba(0, 0, 0, 0.1);
}

.line1 {
  text-align: right;
}

.line2 {
  text-align: left;
}

.line1 div,
.line2 div {
  background-color: #ffffff;
  border-radius: 6px;
}

.image {
  width: 100%;
  height: auto;
  object-fit: contain;
  border: 3px solid #3498db;
  border-radius: 8px;
  box-shadow: 0 4px 8px rgba(0, 0, 0, 0.1);
  margin: 0;
}

.el-col {
  flex: 1;
}

.el-col:last-child {
  flex: 2;
}

.horizontal-row {
  margin-top: 30px;
  display: flex;
  flex-wrap: wrap;
  gap: 20px;
  justify-content: space-between;
  padding: 20px;
  background-color: #f4f4f4;
  border-radius: 12px;
}

.item {
  flex: 1 1 22%;
  min-width: 150px;
  padding: 16px;
  border: 2px solid #3498db;
  border-radius: 10px;
  background-color: #ffffff;
  transition: transform 0.3s ease, box-shadow 0.3s ease;
  font-size: 15px;
  text-align: left;
  box-sizing: border-box;
}

.item:hover {
  transform: translateY(-6px);
  box-shadow: 0 6px 15px rgba(0, 0, 0, 0.15);
}

.circle {
  display: inline-block;
  width: 30px;
  height: 30px;
  line-height: 30px;
  border-radius: 50%;
  background-color: #3498db;
  color: white;
  text-align: center;
  margin-right: 15px;
  font-weight: bold;
  font-size: 18px;
}

hr {
  border: 0;
  height: 3px;
  background-color: #3498db;
  margin: 25px 0;
}   
</style>
