---
title: การติดตั้ง
type: guide
order: 1
vue_version: 2.5.16
gz_size: "30.90"
---

### บันทึกการเข้ากันได้

Vue **ไม่** รองรับ IE8 และต่ำกว่า เพราะว่าใช้ความสามารถของ ECMAScript 5 เนื่องจากไม่รองรับใน IE8 อย่างไรก็ตาม Vue รองรับ [เบาว์เซอร์ที่รองรับ ECMAScript 5](https://caniuse.com/#feat=es5) ทั้งหมด

### บันทึกอัปเดต

เวอร์ชันเสถียรภาพล่าสุด: {{vue_version}}

รายละเอียดบันทึกการอัปเดตของแต่ล่ะเวอร์ชันดูได้ที่ [GitHub](https://github.com/vuejs/vue/releases)

## Vue Devtools

เมื่อใช้ Vue เราแนะนำให้ติดตั้ง [Vue Devtools](https://github.com/vuejs/vue-devtools#vue-devtools) ในเบาว์เซอร์ของคุณ ซึ่งจะทำให้ตรวจสอบและดีบักแอพพลิเคชัน Vue ของได้ใน UI ที่เป็นมิตรต่อผู้ใช้มากขึ้น

## การใช้งาน `<script>` Include

ดาวน์โหลดและ include อย่างง่ายด้วย สคริปท์แท็ก `Vue` จะลงทะเบียนในตัวแปรกลาง

<p class="tip">ห้ามใช้เวอร์ชันแบบง่ายในระหว่างการพัฒนาแอพพลิเคชัน คุณจะพลาดคำเตือนที่มีประโยชน์ของความผิดพลาดที่เกิดขึ้น</p>

<div id="downloads">
<a class="button" href="/js/vue.js" download>เวอร์ชันพัฒนา</a><span class="light info">แสดงคำเตือนทั้งหมดและโหมดดีบัก</span>

<a class="button" href="/js/vue.min.js" download>เวอร์ชันใช้งานจริง</a><span class="light info">คำเตือนถูกซ้อนทั้งหมด ขนาดเล็ก {{gz_size}}KB +gzip</span>
</div>

### CDN

ขอแนะนำให้เชื่อมโยงไปหมายเลขเวอร์ชันที่ต้องการที่คุณสามารถกำหนดได้เอง:

``` html
<script src="https://cdn.jsdelivr.net/npm/vue@2.5.16/dist/vue.js"></script>
```

สามารถเรียกดูแหล่งที่มาของแพคเกจ NPM ได้ที่ [cdn.jsdelivr.net/npm/vue](https://cdn.jsdelivr.net/npm/vue/)

Vue ยังมีอยู่ใน [unpkg](https://unpkg.com/vue@{{vue_version}}/dist/vue.js) และ [cdnjs](https://cdnjs.cloudflare.com/ajax/libs/vue/{{vue_version}}/vue.js) (cdnjs ใช้เวลาในการซิงค์เพื่อให้เป็นเวอร์ชันล่าสุดอาจไม่สามารถใช้งานได้)

ตรวจดูให้แน่ใจว่าอ่านเกี่ยวกับ [การอธิบายความแตกต่างของการสร้างแอพพลิเคชันของ Vue](#Explanation-of-Different-Builds) และใช้ **เวอร์ชันใช้งานจริง** ในเว็บไซท์ แทนที่ `vue.js` ด้วย `vue.min.js` ซี่งเป็นโค้ดที่สร้างขึ้นโดยที่ปรับแต่งเพื่อความเร็วเป็นสำคัญ แทนที่จะเหมาะกับขั้นตอนการพัฒนา

## NPM

NPM เป็นวิธีการที่แนะนำสำหรับสร้างแอพพลิเคชันขนาดใหญ่ด้วย Vue ซึ่งจับคู่กับเครื่องมือรวมชุดโมดูลที่มีประสิทธิภาพอย่างเช่น [Webpack](https://webpack.js.org/) หรือ [Browserify](http://browserify.org/) Vue มีเครื่องมือประกอบให้สำหรับสร้าง [คอมโพแนนต์ไฟล์เดียว](single-file-components.html) 

``` bash
# เวอร์ชันเสถียรล่าสุด
$ npm install vue
```

## CLI

Vue จัดเตรียมเครื่องมือ [CLI เป็นทางการ](https://github.com/vuejs/vue-cli) ให้ สำหรับสร้างโครงโค้ดแอพพลิเคชันเว็บหน้าเดียว ซึ่งจัดขั้นตอนการสร้าง batteries-included สำหรับขั้นตอนการทำงานของ frontend สมัยใหม่ โดยใช้เวลาเพียงไม่กี่นาที่ที่จะสร้างแอพพลิเคชันและทำให้ทำงานได้ด้วย hot-reload, lint-on-save และ production-ready ดูเพิ่มเติมได้ที่ [เอกสาร Vue CLI](https://cli.vuejs.org)

<p class="tip">การใช้งาน CLI จะต้องมีความรู้เกี่ยวกับ Node.js และเครื่องมือสร้างที่เกี่ยวข้อง ถ้าคุณเป็นมือใหม่สำหรับ Vue หรือเครื่องมือสร้าง frontend แล้ว เราแนะนำให้อ่าน <a href="./">คำแนะนำ</a> ก่อน โดยไม่ต้องใช้เครื่องมือสร้าง CLI</p>

## การอธิบายความแตกต่างของการสร้างแอพพลิเคชัน

ใน [ไดเรกทอรีของเพกเกจ NPM `dist/`](https://cdn.jsdelivr.net/npm/vue/dist/) จะเจอความแตกต่างหลายอย่างของการสร้างของ Vue.js ซึ่งแสดงภาพรวมของความแตกต่างของการสร้างดังนี้:

| | UMD | CommonJS | ES Module |
| --- | --- | --- | --- |
| **Full** | vue.js | vue.common.js | vue.esm.js |
| **Runtime-only** | vue.runtime.js | vue.runtime.common.js | vue.runtime.esm.js |
| **Full (production)** | vue.min.js | - | - |
| **Runtime-only (production)** | vue.runtime.min.js | - | - |

### ข้อกำหนด

- **Full**: การสร้างที่บรรจุทั้ง compiler และ runtime

- **Compiler**: โค้ดที่รับผิดชอบสำหรับรวบรวมเทมเพลตข้อความไปยังฟังก์ชันแสดงผล JavaScript

- **Runtime**: โค้ดที่รับผิดชอบสำหรับสร้างอินสแตนส์ของ Vue, แสดงผลและแก้ไข DOM เสมือน เป็นต้น. โดยพื้นฐานแล้วการสร้างแบบนี้จะสร้างทุกสิ่งทุกอย่างยกเว้น Compiler

- **[UMD](https://github.com/umdjs/umd)**: การสร้างแบบ UMD สามารถใช้เพื่อสร้างไดเรกทอรีในเว็บบราวเซอร์ด้วย แท็ก `<script>` ไฟล์เริ่มต้นจาก jsDeliver CDN ที่ [https://cdn.jsdelivr.net/npm/vue](https://cdn.jsdelivr.net/npm/vue) เป็น Runtime + Compiler UMD build (`vue.js`)

- **[CommonJS](http://wiki.commonjs.org/wiki/Modules/1.1)**: การสร้างแบบ CommonJS เป็นการสร้างที่ใช้สำหรับตัวรวมชุดโมดูลแบบเก่า เช่น [browserify](http://browserify.org/) หรือ [webpack 1](https://webpack.github.io) ไฟล์เริ่มต้นสำหรับตัวรวบรวมโมดูลคือ (`pkg.mian`) เป็น Runtime CommonJS build (`vue.runtime.common.js`) เท่านั้น

- **[ES Module](http://exploringjs.com/es6/ch_modules.html)**: การสร้างแบบ ES module เป็นการสร้างที่ใช้สำหรับตัวรวมชุดโมดูลแบบใหม่ เช่น [webpack 2](https://webpack.js.org) หรือ [rollup](https://rollupjs.org/) ไฟล์เริ่มต้นสำหรับตัวรวมรวมโมดูลคือ (`pkg.module`) เป็น Runtime ES Module build เท่านั้น (`vue.runtime.esm.js`)

### Runtime + Compiler vs. Runtime-only

ถ้าคุณต้องการเทมเพลตการสร้างบนเครื่องไคลเอน (ตัวอย่างเช่น ส่งผ่านข้อความไปที่ตัวเลือก `template` หรือ การผูกส่วนประกอบต่างๆ ด้วย in-DOM HTML เป็นเทมเพลต) คุณจำเป็นต้องใช้คอมไฟล์เลอร์และการสร้างแบบ Full

``` js
// ต้องใช้คอมไฟล์เลอร์
new Vue({
  template: '<div>{{ hi }}</div>'
})

// ไม่ต้องใช้คอมไฟล์เลอร์
new Vue({
  render (h) {
    return h('div', this.hi)
  }
})
```

เมื่อใช้ `vue-loader` หรือ `vueify` เทมเพลตข้างในไฟล์ `*.vue` เป็นโค้ดก่อนรวบรวมเป็น JavaScript ขณะเวลาสร้าง คุณไม่ต้องการคอมไฟล์เลอร์จริงๆในการรวมรวมขั้นสุดท้าย และสามารถใช้การสร้างในรันไทม์เท่านั้น 

ในเมื่อการสร้างในรันไทม์เท่านั้นจะได้ไฟล์มีขนาดเพียงประมาณ 30% ของการสร้างแบบเต็ม ควรใช้การสร้างแบบนี้ทุกครั้งที่ทำได้ และถ้าคุณต้องการใช้การสร้างแบบเต็มแทน คุณแค่ตั้งค่าในตัวรวมรวมโมดูลของคุณ

#### Webpack

``` js
module.exports = {
  // ...
  resolve: {
    alias: {
      'vue$': 'vue/dist/vue.esm.js' // 'vue/dist/vue.common.js' for webpack 1
    }
  }
}
```

#### Rollup

``` js
const alias = require('rollup-plugin-alias')

rollup({
  // ...
  plugins: [
    alias({
      'vue': 'vue/dist/vue.esm.js'
    })
  ]
})
```

#### Browserify

เพิ่มโค้ดนี้ไปยัง `package.json` ในโปรเจคของคุณ:

``` js
{
  // ...
  "browser": {
    "vue": "vue/dist/vue.common.js"
  }
}
```

#### Parcel

เพิ่มโค้ดนี้ไปยัง `package.json` ในโปรเจคของคุณ:

``` js
{
  // ...
  "alias": {
    "vue" : "./node_modules/vue/dist/vue.common.js"
  }
}
```

### โหมด การพัฒนา vs. การนำไปใช้งานจริง

โหมด การพัฒนา(Development) และการนำไปใช้งานจริง (Production) เป็น hard-coded สำหรับการสร้างแบบ UMD: เป็นการสร้างแอพพลิเคชันที่ไม่ลดขนาดของไฟล์สำหรับการพัฒนา และลดขนาดของไฟล์สำหรับการนำไปใช้จริง

การสร้าง CommonJS และ ES Modules เป็นหน้าที่ของตัวรวบรวมโมดูล ดังนั้นเราไม่สามารถลดขนาดของไฟล์เหลานี้ได้ ซึ่งคุณสามารถลดขนาดของมันได้โดยการตั้งค่าในตัวรวบรวมโมดูลด้วยตัวคุณเอง

การสร้าง CommonJS และ ES Modules ยังสงวนสำหรับการตรวจสอบ `process.env.NODE_ENV` เพื่อกำหนดโหมดที่จะรัน คุณควรจะใช้การตั้งค่าของตัวรวบรวมโมดูลที่เหมาะสมไปแทนที่ตัวแปลของสิ่งแวดล้อมระบบเพื่อจะควบคุมว่าโหมดไหม Vue ควรจะรัน การแทนที่ `process.env.NODE_ENV` ด้วยการตั้งค่าทำให้ลดขนาดของไฟล์ได้ เช่น UglifyJS เพื่อเอาไฟล์ของโหมดพัฒนาออกทำให้ขนาดของไฟล์เล็กลง

#### Webpack

ใน Webpack 4+, คุณสามารถใช้โหลดตัวเลือก `mode`:

``` js
module.exports = {
  mode: 'production'
}
```

แต่ใน Webpack 3 และเวอร์ชันก่อนหน้า คุณจำเป็นต้องใช้ [DefinePlugin](https://webpack.js.org/plugins/define-plugin/):

``` js
var webpack = require('webpack')

module.exports = {
  // ...
  plugins: [
    // ...
    new webpack.DefinePlugin({
      'process.env': {
        NODE_ENV: JSON.stringify('production')
      }
    })
  ]
}
```

#### Rollup

ใช้ [rollup-plugin-replace](https://github.com/rollup/rollup-plugin-replace):

``` js
const replace = require('rollup-plugin-replace')

rollup({
  // ...
  plugins: [
    replace({
      'process.env.NODE_ENV': JSON.stringify('production')
    })
  ]
}).then(...)
```

#### Browserify

ใช้ global [envify](https://github.com/hughsk/envify) แปลงไปยังตัวรวบควมโมดูลของคุณ

``` bash
NODE_ENV=production browserify -g envify -e main.js | uglifyjs -c -m > build.js
```

ดูเพิ่มเติมได้ที่ [เคล็ดลับในการพัฒนาการนำไปใช้งาน](deployment.html).

### สิ่งแวดล้อม CSP

บางสิ่งแวดล้อม อย่่างเช่น Google Chrome Apps บังคับใช้ นโยบายความปลอดภัยของเนื้อหา (Content Security Policy: CPS) โดยการห้ามมิให้ใช้ `new Function()` สำหรับการประเมินนิพจน์ การสร้างแบบเต็มขึ้นอยู่กับคุณลักษณะเพื่อคอมไฟล์เทมเพลต ดังนั้นจึงไม่สามารถใช้งานได้ในสิ่งแวดล้อมเหลานี้

ในทางกลับกัน การสร้งแบบ runtime-only สอดคล้องกับ CSP เต็มรูปแบบ เมื่อใช้การสร้างแบบ runtime-only ด้วย [Webpack + vue-loader](https://github.com/vuejs-templates/webpack-simple) หรือ [Browserify + vueify](https://github.com/vuejs-templates/browserify-simple) เทมเพลตของคุณจะต้องฟรีคอมไฟล์ไปเป็นฟังก์ชัน `render` ซึ่งทำงานอย่างยอดเยี่ยมกับสิ่งแวดล้อม CSP

## การสร้างในขั้นตอนพัฒนา

**สำคัญ**: การสร้างไฟล์ใน GitHub โฟลเดอร์ `/dist` เป็นการเช็คอินเฉพาะในระหว่าง releases เพื่อใช้ Vue จากซอร์ซโค้ดบน GitHub คุณสามารถสร้างได้ด้วยตัวคุณเอง

``` bash
git clone https://github.com/vuejs/vue.git node_modules/vue
cd node_modules/vue
npm install
npm run build
```

## Bower

เพียงการสร้าง UMD ใช้ได้จาก Bower

``` bash
# เวอร์ชันเสถียรล่าสุด
$ bower install vue
```

## ตัวโหลดโมดูล AMD

การสร้างแบบ UMD ทั้งหมดสามารถใช้ได้โดยตรงแบบโมดูล ​AMD
All UMD builds can be used directly as an AMD module.
