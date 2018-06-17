---
title: เอพีไอ
type: api
---

## Global Config

`Vue.config` เป็นวัตถุที่มีการกำหนดค่าทั่วโลกของ Vue คุณสามารถแก้ไขคุณสมบัติของรายการด้านล่างก่อนที่จะบูตแอ็พพลิเคชันของคุณ:

### silent

- **ประเภท:** `boolean`

- **ค่าเริ่มต้น:** `false`

- **การใช้งาน:**

  ``` js
  Vue.config.silent = true
  ```

  ยกเลิกการบันทึกและคำเตือน Vue ทั้งหมด

### optionMergeStrategies

- **ประเภท:** `{ [key: string]: Function }`

- **ค่าเริ่มต้น:** `{}`

- **การใช้งาน:**

  ``` js
  Vue.config.optionMergeStrategies._my_option = function (parent, child, vm) {
    return child + 1
  }

  const Profile = Vue.extend({
    _my_option: 1
  })

  // Profile.options._my_option = 2
  ```

  กำหนดกลยุทธ์การผสานที่กำหนดเองสำหรับตัวเลือก

  ยุบตารางนี้ขยายตารางนี้กลยุทธ์การผสานได้รับค่าของอ็อพชันที่กำหนดไว้ในอินสแตนซ์ระดับบนสุดและอันดับที่สองตามลำดับ อินสแตนซ์ Vue ของบริบทถูกส่งผ่านเป็นอาร์กิวเมนต์ที่สาม

- **ดูเพิ่มเติม:** [กลยุทธ์การรวมกลยุทธ์ที่ผันผวน](../guide/mixins.html#Custom-Option-Merge-Strategies)

### devtools

- **ประเภท:** `boolean`

- **ค่าเริ่มต้น:** `true` (`false` in production builds)

- **การใช้งาน:**

  ``` js
  //ตรวจสอบให้แน่ใจว่าได้ตั้งค่านี้พร้อมกันทันทีหลังจากโหลด Vue
  Vue.config.devtools = true
  ```

  กำหนดค่าว่าจะอนุญาต [vue-devtools](https://github.com/vuejs/vue-devtools) inspection. ค่าเริ่มต้นของตัวเลือกนี้เป็น `true`ในการสร้างการพัฒนาและ `false` ในการสร้างการผลิต คุณสามารถกำหนดให้เป็น `true` เพื่อเปิดใช้งานการตรวจสอบสำหรับการสร้างการผลิต

### errorHandler

- **ประเภท:** `Function`

- **ค่าเริ่มต้น:** `undefined`

- **การใช้งาน:**

  ``` js
  Vue.config.errorHandler = function (err, vm, info) {
    // handle error
    // `info` is a Vue-specific error info, e.g. which lifecycle hook
    // the error was found in. Only available in 2.2.0+
  }
  ```

  กำหนดตัวจัดการข้อผิดพลาดที่ไม่สามารถตรวจจับได้ระหว่างฟังก์ชันการแสดงผลและตัวแสดงส่วนประกอบ ตัวจัดการได้รับการเรียกด้วยข้อผิดพลาดและอินสแตนซ์ Vue

  > In 2.2.0+, this hook also captures errors in component lifecycle hooks. Also, when this hook is `undefined`, captured errors will be logged with `console.error` instead of crashing the app.

  > In 2.4.0+ this hook also captures errors thrown inside Vue custom event handlers.

  > บริการติดตามข้อผิดพลาด [Sentry](https://sentry.io/for/vue/) และ [Bugsnag](https://docs.bugsnag.com/platforms/browsers/vue/) ให้การผสานรวมอย่างเป็นทางการโดยใช้ตัวเลือกนี้

### warnHandler

> New in 2.4.0+

- **ประเภท:** `Function`

- **ค่าเริ่มต้น:** `undefined`

- **การใช้งาน:**

  ``` js
  Vue.config.warnHandler = function (msg, vm, trace) {
    // `trace` คือการตรวจสอบลำดับชั้นคอมโพเนนต์
  }
  ```

  กำหนดตัวจัดการที่กำหนดเองสำหรับคำเตือน Vue รันไทม์ โปรดทราบว่าสิ่งนี้ใช้ได้เฉพาะในระหว่างการพัฒนาและถูกละเลยในการผลิต

### ignoredElements

- **ประเภท:** `Array<string | RegExp>`

- **ค่าเริ่มต้น:** `[]`

- **การใช้งาน:**

  ``` js
  Vue.config.ignoredElements = [
    'my-custom-web-component',
    'another-web-component',
    // ใช้ "RegExp" เพื่อละเว้นองค์ประกอบทั้งหมด ที่ขึ้นต้นด้วย "ion-"
    // 2.5+ only
    /^ion-/
  ]
  ```

  ทำให้ Vue ละเว้นองค์ประกอบที่กำหนดเองที่กำหนดไว้ด้านนอกของ Vue (เช่นการใช้ Web Components APIs) มิฉะนั้นจะเป็นการเตือนเกี่ยวกับ `Unknown custom element`, สมมติว่าคุณลืมที่จะลงทะเบียนคอมโพเนนต์ส่วนกลางหรือสะกดชื่อคอมโพเนนต์

### keyCodes

- **ประเภท:** `{ [key: string]: number | Array<number> }`

- **ค่าเริ่มต้น:** `{}`

- **การใช้งาน:**

  ``` js
  Vue.config.keyCodes = {
    v: 86,
    f1: 112,
    // camelCase จะไม่ทำงาน
    mediaPlayPause: 179,
    // คุณสามารถใช้ kebab-case กับเครื่องหมาย double quotation 
    "media-play-pause": 179,
    up: [38, 87]
  }
  ```

  ```html
  <input type="text" @keyup.media-play-pause="method">
  ```

  กำหนดนามแฝงคีย์ที่กำหนดเอง (es) สำหรับ `v-on`.

### ประสิทธิภาพ

> New in 2.2.0+

- **ประเภท:** `boolean`

- **ค่าเริ่มต้น:** `false (from 2.2.3+)`

- **การใช้งาน**:

  ตั้งค่านี้เป็น `true` เปิดใช้งานคอมโพเนนต์ init เรียบเรียงทำให้เดสก์ท็อปและแก้ไขการสืบค้นกลับประสิทธิภาพในแถบประสิทธิภาพ / ไทม์ไลน์ของเบราว์เซอร์ devtool ใช้งานได้เฉพาะในโหมดการพัฒนาและในเบราว์เซอร์ที่สนับสนุน API [performance.mark](https://developer.mozilla.org/en-US/docs/Web/API/Performance/mark) API.

### productionTip

> New in 2.2.0+

- **ประเภท:** `boolean`

- **ค่าเริ่มต้น:** `true`

- **การใช้งาน**:

  ตั้งค่านี้เป็น `false` เพื่อป้องกันไม่ให้เคล็ดลับการผลิตเมื่อเริ่มต้นใช้งาน Vue

## Global API

### Vue.extend( ตัวเลือก )

- **อาร์กิวเมนต์:**
  - `{Object} options`

- **การใช้งาน:**

  การสร้าง "subclass" ของตัวสร้างฐาน Vue อาร์กิวเมนต์ควรเป็นอ็อบเจ็กต์ที่ประกอบด้วยตัวเลือกคอมโพเนนต์

  กรณีพิเศษที่จะต้องทราบที่นี่เป็น `data` ตัวเลือก - จะต้องมีฟังก์ชั่นเมื่อใช้กับ `Vue.extend()`.

  ``` html
  <div id="mount-point"></div>
  ```

  ``` js
  // สร้าง constructor
  var Profile = Vue.extend({
    template: '<p>{{firstName}} {{lastName}} aka {{alias}}</p>',
    data: function () {
      return {
        firstName: 'Walter',
        lastName: 'White',
        alias: 'Heisenberg'
      }
    }
  })
  // สร้างอินสแตนซ์ของ Profile และติดตั้งบน element
  new Profile().$mount('#mount-point')
  ```

  จะส่งผลให้:

  ``` html
  <p>Walter White aka Heisenberg</p>
  ```

- **ดูเพิ่มเติมที่:** [คอมโพเนนต์](../guide/components.html)

### Vue.nextTick( [callback, context] )

- **อาร์กิวเมนต์:**
  - `{Function} [callback]`
  - `{Object} [context]`

- **การใช้งาน:**

  เลื่อนการเรียกกลับที่จะดำเนินการหลังจากรอบการอัพเดท DOM ครั้งต่อไป ใช้ทันทีหลังจากที่คุณได้เปลี่ยนข้อมูลบางส่วนเพื่อรอการอัปเดต DOM

  ``` js
  // แก้ไขข้อมูล
  vm.msg = 'Hello'
  // DOM ยังไม่ได้อัพเดต
  Vue.nextTick(function () {
    // ปรับปรุง DOM แล้ว
  })

  // usage as a promise (2.1.0+, see note below)
  Vue.nextTick()
    .then(function () {
      // ปรับปรุง DOM แล้ว
    })
  ```

  > ใน 2.1.0+: ส่งกลับ Promise ถ้าไม่มีการเรียกกลับและ Promise ได้รับการสนับสนุนในสภาพแวดล้อมการทำงาน โปรดทราบว่า Vue ไม่ได้มี Promise polyfill ดังนั้นหากคุณกำหนดเป้าหมายเบราว์เซอร์ที่ไม่สนับสนุน Promises natively (กำลังมองหาคุณ IE) คุณจะต้องจัดหา polyfill ด้วยตนเอง

- **ดูเพิ่มเติมที่:** [Async Update Queue](../guide/reactivity.html#Async-Update-Queue)

### Vue.set( target, key, value )

- **อาร์กิวเมนต์:**
  - `{Object | Array} target`
  - `{string | number} key`
  - `{any} value`

- **ส่งกลับ:** ค่าที่ตั้งไว้

- **การใช้งาน:**

  เพิ่มคุณสมบัติลงในออบเจกต์เชิงโต้ตอบเพื่อให้มั่นใจว่าพร็อพเพอร์ตี้ใหม่ยังเป็นปฏิกิริยาดังนั้นเรียกดูการอัปเดต ต้องใช้คุณสมบัตินี้เพื่อเพิ่มคุณสมบัติใหม่ให้กับวัตถุที่มีปฏิกิริยาเช่น Vue ไม่สามารถตรวจหาการเพิ่มคุณสมบัติตามปกติ  (เช่น `this.myObject.newProperty = 'hi'`).

  <p class="tip">อ็อบเจ็กต์เป้าหมายไม่สามารถเป็นอินสแตนซ์ Vue หรืออ็อบเจ็กต์ข้อมูลหลักของอินสแตนซ์ Vue</p>

- **ดูเพิ่มเติม:** [Reactivity in Depth](../guide/reactivity.html)

### Vue.delete( target, key )

- **อาร์กิวเมนต์:**
  - `{Object | Array} target`
  - `{string | number} key/index`

  > เฉพาะใน 2.2.0+: ใช้งานได้กับดัชนี Array + เท่านั้น

- **การใช้งาน:**

  ลบคุณสมบัติบนวัตถุ ถ้าวัตถุเป็นปฏิกิริยาให้แน่ใจว่าการลบเรียกดูการปรับปรุง นี่ใช้เป็นหลักเพื่อหลีกเลี่ยงข้อ จำกัด ที่ Vue ไม่สามารถตรวจพบการลบคุณสมบัติได้ แต่คุณไม่จำเป็นต้องใช้บ่อยนัก

  <p class="tip">อ็อบเจ็กต์เป้าหมายไม่สามารถเป็นอินสแตนซ์ Vue หรืออ็อบเจ็กต์ข้อมูลหลักของอินสแตนซ์ Vue</p>

- **ดูเพิ่มเติม:** [Reactivity in Depth](../guide/reactivity.html)

### Vue.directive( id, [definition] )

- **อาร์กิวเมนต์:**
  - `{string} id`
  - `{Function | Object} [definition]`

- **การใช้งาน:**

  ลงทะเบียนหรือเรียกค้นคำสั่งระดับโลก

  ``` js
  // ลงทะเบียน
  Vue.directive('my-directive', {
    bind: function () {},
    inserted: function () {},
    update: function () {},
    componentUpdated: function () {},
    unbind: function () {}
  })

  // ลงทะเบียน (function directive)
  Vue.directive('my-directive', function () {
    // this will be called as `bind` and `update`
  })

  // getter, ส่งกลับคำนิยาม directive ถ้า
  var myDirective = Vue.directive('my-directive')
  ```

- **ดูเพิ่มเติมที่:** [Custom Directives](../guide/custom-directive.html)

### Vue.filter( id, [definition] )

- **อาร์กิวเมนต์:**
  - `{string} id`
  - `{Function} [definition]`

- **การใช้งาน:**

  ลงทะเบียนหรือเรียกใช้ตัวกรองทั่วโลก

  ``` js
  // ลงทะเบียน
  Vue.filter('my-filter', function (value) {
    // return processed value
  })

  // getter ส่งคืนตัวกรอง ถ้า var ลงทะเบียน
  var myFilter = Vue.filter('my-filter')
  ```

- **ดูเพิ่มเติมที่:** [Filters](../guide/filters.html)

### Vue.component( id, [definition] )

- **อาร์กิวเมนต์:**
  - `{string} id`
  - `{Function | Object} [definition]`

- **การใช้งาน:**

  ลงทะเบียนหรือเรียกใช้คอมโพเนนต์ส่วนกลาง การลงทะเบียนอัตโนมัติ จะกำหนดส่วนประกอบของ `name` กับที่กำหนด `id`.

  ``` js
  // ลงทะเบียนขยาย constructor
  Vue.component('my-component', Vue.extend({ /* ... */ }))

  // ลงทะเบียนวัตถุออบเจ็กต์ (โดยอัตโนมัติเรียก Vue.extend)
  Vue.component('my-component', { /* ... */ })

  // เรียกคืนคอมโพเนนต์ที่ลงทะเบียน (ส่งค่า constructor กลับเสมอ)
  var MyComponent = Vue.component('my-component')
  ```

- **ดูเพิ่มเติมที่:** [คอมโพเนนต์](../guide/components.html)

### Vue.use( plugin )

- **อาร์กิวเมนต์:**
  - `{Object | Function} plugin`

- **การใช้งาน:**

  ติดตั้งปลั๊กอิน Vue.js หากปลั๊กอินเป็น Object จะต้องเปิดเผย `install` วิธีการ ถ้าเป็นฟังก์ชันเองจะถือว่าเป็นวิธีการติดตั้ง วิธีการติดตั้งจะเรียกว่า Vue เป็นอาร์กิวเมนต์

  เมื่อใช้เมธอดนี้ในปลั๊กอินเดียวกันหลายครั้งปลั๊กอินจะถูกติดตั้งเพียงครั้งเดียว

- **ดูเพิ่มเติมที่:** [Plugins](../guide/plugins.html)

### Vue.mixin( mixin )

- **อาร์กิวเมนต์:**
  - `{Object} mixin`

- **การใช้งาน:**

  ใช้ mixin ทั่วโลกซึ่งมีผลกับอินสแตนซ์ Vue ทุกตัวที่สร้างขึ้นหลังจากนั้น ซึ่งสามารถใช้โดยผู้เขียนปลั๊กอินเพื่อแทรกลักษณะการทำงานที่กำหนดเองลงในคอมโพเนนต์ ไม่แนะนำให้ใช้ในรหัสแอพลิเคชัน **ไม่แนะนำให้ใช้ในรหัสแอพลิเคชัน**.

- **ดูเพิ่มเติม:** [Global Mixin](../guide/mixins.html#Global-Mixin)

### Vue.compile( template )

- **อาร์กิวเมนต์:**
  - `{string} template`

- **การใช้งาน:**

  คอมไพล์สตริงเทมเพลตในฟังก์ชันการแสดงผล **ใช้ได้เฉพาะในเวอร์ชันเต็ม**

  ``` js
  var res = Vue.compile('<div><span>{{ msg }}</span></div>')

  new Vue({
    data: {
      msg: 'hello'
    },
    render: res.render,
    staticRenderFns: res.staticRenderFns
  })
  ```

- **ดูเพิ่มเติมที่:** [Render Functions](../guide/render-function.html)

### Vue.version

- **รายละเอียด**: ระบุเวอร์ชั่นที่ติดตั้ง Vue เป็นสตริง นี่เป็นประโยชน์อย่างยิ่งสำหรับปลั๊กอินและส่วนประกอบของชุมชนซึ่งคุณอาจใช้กลยุทธ์ที่แตกต่างกันสำหรับเวอร์ชันต่างๆ

- **การใช้งาน**:

  ```js
  var version = Number(Vue.version.split('.')[0])

  if (version === 2) {
    // Vue v2.x.x
  } else if (version === 1) {
    // Vue v1.x.x
  } else {
    // Vue ที่ไม่ได้รับการสนับสนุน
  }
  ```

## ตัวเลือก / ข้อมูล

### ข้อมูล

- **ประเภท:** `Object | Function`

- **ข้อจำกัด:** เฉพาะ `Function` เมื่อใช้ในนิยามคอมโพเนนต์

- **รายละเอียด:**

  อ็อบเจ็กต์ข้อมูลสำหรับอินสแตนซ์ Vue Vue จะแปลงค่าคุณสมบัติให้เป็น recursively ใน getter / setters เพื่อให้เป็น "reactive" **Object ต้องเป็นแบบธรรมดา**: ออบเจ็กต์ดั้งเดิมเช่นออบเจ็กต์ API ของเบราว์เซอร์และคุณสมบัติต้นแบบจะถูกละเลย กฎของหัวแม่มือคือข้อมูลควรจะเป็นข้อมูล - ไม่ควรสังเกตวัตถุที่มีพฤติกรรมเป็นของตัวเอง.

  เมื่อสังเกตแล้วคุณจะไม่สามารถเพิ่มคุณสมบัติปฏิกิริยาต่อกับอ็อบเจ็กต์ข้อมูลรากอีกต่อไป ขอแนะนำให้ประกาศล่วงหน้าคุณสมบัติระดับการตอบสนองระดับรากทั้งหมดก่อนที่จะสร้างอินสแตนซ์

  หลังจากสร้างอินสแตนซ์แล้วคุณสามารถเข้าถึงอ็อบเจ็กต์ข้อมูลเดิมได้ เช่น `vm.$data`. อินสแตนซ์ Vue ยังพร็อกซีคุณสมบัติทั้งหมดที่พบในอ็อบเจ็กต์ข้อมูลเช่นกัน `vm.a` จะเท่ากับ `vm.$data.a`.

  คุณสมบัติที่ขึ้นต้นด้วย `_` หรือ `$` จะ **ไม่** ถูก proxied ในตัวอย่าง Vue เนื่องจากอาจขัดแย้งกับคุณสมบัติภายในของ Vue และวิธี API คุณจะต้องเข้าถึงพวกเขาเป็น `vm.$data._property`.

  เมื่อกำหนดคอมโพเนนต์ **component**, `data` ต้องประกาศเป็นฟังก์ชันที่ส่งคืนออบเจ็กต์ข้อมูลเริ่มต้นเนื่องจากจะมีหลายอินสแตนซ์ที่สร้างโดยใช้คำจำกัดความเดียวกัน ถ้าเราใช้วัตถุธรรมดาสำหรับ `data`, วัตถุเดียวกันนั้นจะเป็น **shared by reference** ข้ามทุกกรณีที่สร้างขึ้น โดยการให้ฟังก์ชั่น `data` , ทุกครั้งที่สร้างอินสแตซ์ใหม่ เราสามารถเรียกใช้ได้ เพื่อส่งคืนข้อมูลเริ่มต้น

  หากจำเป็นต้องใช้โคลนลึกของวัตถุต้นฉบับได้ โดยการ passing `vm.$data` ผ่าน `JSON.parse(JSON.stringify(...))`.

- **ตัวอย่าง:**

  ``` js
  var data = { a: 1 }

  // การสร้างอินสแตนซ์โดยตรง
  var vm = new Vue({
    data: data
  })
  vm.a // => 1
  vm.$data === data // => true

  // ต้องใช้ฟังก์ชันเมื่ออยู่ใน Vue.extend()
  var Component = Vue.extend({
    data: function () {
      return { a: 1 }
    }
  })
  ```

  ถ้าคุณใช้ฟังก์ชัน arrow กับคุณสมบัติ `data` , `this` จะไม่เป็นอินสแตนซ์ของคอมโพเนนต์ แต่คุณยังคงสามารถเข้าถึงอินสแตนซ์เป็นอาร์กิวเมนต์แรกของฟังก์ชัน:

  ```js
  data: vm => ({ a: vm.myProp })
  ```

- **ดูเพิ่มเติม:** [Reactivity in Depth](../guide/reactivity.html)

### ส่งผ่าน

- **ประเภท:** `Array<string> | Object`

- **รายละเอียด:**

  รายการ / แฮชของแอ็ตทริบิวต์ที่รับข้อมูลจากคอมโพเนนต์หลัก มีไวยากรณ์ที่ใช้ Array และไวยากรณ์ Object-based ซึ่งจะช่วยให้สามารถกำหนดค่าขั้นสูงเช่นการตรวจสอบชนิดการตรวจสอบความถูกต้องและค่าดีฟอลต์

- **ตัวอย่าง:**

  ``` js
  // ไวยากรณ์ง่ายๆ
  Vue.component('props-demo-simple', {
    props: ['size', 'myMessage']
  })

  // รูปแบบวัตถุที่มีการตรวจสอบ
  Vue.component('props-demo-advanced', {
    props: {
      // ตรวจสอบ
      height: Number,
      // ตรวจสอบประเภท 
      age: {
        type: Number,
        default: 0,
        required: true,
        validator: function (value) {
          return value >= 0
        }
      }
    }
  })
  ```

- **ดูเพิ่มเติม:** [Props](../guide/components.html#Props)

### propsData

- **ประเภท:** `{ [key: string]: any }`

- **ข้อจำกัด:** การใช้งานเฉพาะในการสร้างอินสแตนซ์ผ่าน `new`.

- **รายละเอียด:**

  ส่งพร็อพไปยังอินสแตนซ์ระหว่างการสร้าง นี้มีวัตถุประสงค์หลักเพื่อให้การทดสอบหน่วยง่ายขึ้น

- **ตัวอย่าง:**

  ``` js
  var Comp = Vue.extend({
    props: ['msg'],
    template: '<div>{{ msg }}</div>'
  })

  var vm = new Comp({
    propsData: {
      msg: 'hello'
    }
  })
  ```

### คำนวณ

- **ประเภท:** `{ [key: string]: Function | { get: Function, set: Function } }`

- **รายละเอียด:**

  คุณสมบัติเชิงคำนวณที่จะผสมลงในตัวอย่าง Vue getters ทั้งหมดและ setters มีของพวกเขา `this` บริบทเชื่อมโยงกับอินสแตนซ์ Vue โดยอัตโนมัติ

  ถ้าคุณใช้ฟังก์ชัน arrow กับคุณสมบัติที่คำนวณ `this` จะไม่เป็นอินสแตนซ์ของคอมโพเนนต์ แต่คุณยังคงสามารถเข้าถึงอินสแตนซ์นี้เป็นอาร์กิวเมนต์แรกของฟังก์ชัน:

  ```js
  computed: {
    aDouble: vm => vm.a * 2
  }
  ```

  คุณสมบัติเชิงคำนวณจะถูกแคชและคำนวณใหม่เฉพาะเมื่อมีการเปลี่ยนแปลงการอ้างอิงขึ้น โปรดทราบว่าถ้าพึ่งพาอยู่นอกขอบเขตของอินสแตนซ์ (เช่น not reactive), คุณสมบัติที่คำนวณจะไม่ได้รับการปรับปรุง

- **ตัวอย่าง:**

  ```js
  var vm = new Vue({
    data: { a: 1 },
    computed: {
      // ได้รับอย่างเดียว
      aDouble: function () {
        return this.a * 2
      },
      // ทั้งสองได้รับและตั้งค่า
      aPlus: {
        get: function () {
          return this.a + 1
        },
        set: function (v) {
          this.a = v - 1
        }
      }
    }
  })
  vm.aPlus   // => 2
  vm.aPlus = 3
  vm.a       // => 2
  vm.aDouble // => 4
  ```

- **ดูเพิ่มเติม:** [Computed Properties](../guide/computed.html)

### เมธอด

- **ประเภท:** `{ [key: string]: Function }`

- **รายละเอียด:**

  วิธีการผสมลงในตัวอย่าง Vue คุณสามารถเข้าถึงวิธีการเหล่านี้ได้โดยตรงจากอินสแตนซ์ของ VM หรือใช้ในการแสดงคำสั่ง วิธีการทั้งหมดจะมี `this` บริบทเชื่อมโยงกับอินสแตนซ์ Vue โดยอัตโนมัติ

  <p class="tip">โปรดทราบว่า คุณไม่ควรใช้ฟังก์ชัน arrow เพื่อกำหนดเมธอด (เช่น `plus: () => this.a++`). เหตุผลก็คือฟังก์ชันลูกศรผูกบริบทหลัก ดังนั้น `this` จะไม่เป็นตัวอย่าง Vue ตามที่คุณคาดหวังและ `this.a` จะไม่ได้กำหนดไว้</p>

- **ตัวอย่าง:**

  ```js
  var vm = new Vue({
    data: { a: 1 },
    methods: {
      plus: function () {
        this.a++
      }
    }
  })
  vm.plus()
  vm.a // 2
  ```

- **ดูเพิ่มเติม:** [Event Handling](../guide/events.html)

### watch

- **ประเภท:** `{ [key: string]: string | Function | Object | Array}`

- **รายละเอียด:**

  วัตถุที่คีย์เป็นนิพจน์เพื่อดูและค่าคือการเรียกกลับที่ตรงกัน ค่านี้อาจเป็นสตริงชื่อเมธอดหรือ Object ที่มีตัวเลือกเพิ่มเติม อินสแตนซ์ Vue จะเรียก `$watch()` ใช้งานแต่ละรายการในอ็อบเจ็กต์ที่ instantiation

- **ตัวอย่าง:**

  ``` js
  var vm = new Vue({
    data: {
      a: 1,
      b: 2,
      c: 3,
      d: 4,
      e: {
        f: {
          g: 5
        }
      }
    },
    watch: {
      a: function (val, oldVal) {
        console.log('new: %s, old: %s', val, oldVal)
      },
      // ชื่อเมธอดสตริง
      b: 'someMethod',
      // เฝ้าระวัง
      c: {
        handler: function (val, oldVal) { /* ... */ },
        deep: true
      },
      // callback จะเรียกทันทีหลังจากเริ่มสังเกต
      d: {
        handler: function (val, oldVal) { /* ... */ },
        immediate: true
      },
      e: [
        function handle1 (val, oldVal) { /* ... */ },
        function handle2 (val, oldVal) { /* ... */ }
      ],
      // ดูค่าของ vm.e.f's : {g: 5}
      'e.f': function (val, oldVal) { /* ... */ }
    }
  })
  vm.a = 2 // => new: 2, old: 1
  ```

  <p class="tip">คุณไม่ควรใช้ฟังก์ชัน arrow เพื่อกำหนดตัวเฝ้า (เช่น `searchQuery: newValue => this.updateAutocomplete(newValue)`). สาเหตุที่ฟังก์ชัน arrow ผูกบริบทหลัก ดังนั้น `this` จะไม่เป็นตัวอย่าง Vue ตามที่คุณคาดหวังและ `this.updateAutocomplete` จะไม่ได้กำหนดไว้</p>

- **ดูเพิ่มเติม:** [Instance Methods / Data - vm.$watch](#vm-watch)

## ตัวเลือก / DOM

### el

- **ประเภท:** `string | HTMLElement`

- **ข้อจำกัด:** การใช้งานเฉพาะในการสร้างอินสแตนซ์ผ่าน `new`.

- **รายละเอียด:**

  ระบุอินสแตนซ์ DOM ของ DOM ที่มีอยู่ให้กับอินสแตนซ์ Vue อาจเป็นสตริง selector CSS หรือ HTMLElement ที่เกิดขึ้นจริง

  หลังจากที่อินสแตนซ์ที่ติดตั้งองค์ประกอบการแก้ไขจะสามารถเข้าถึงได้เป็น `vm.$el`.

  ถ้าตัวเลือกนี้พร้อมใช้งานที่ instantiation อินสแตนซ์จะเข้าสู่การรวบรวมทันที มิฉะนั้นผู้ใช้จะต้องเรียกอย่างชัดแจ้ง `vm.$mount()` เพื่อเริ่มคอมไพล์ด้วยตัวเอง

  <p class="tip">องค์ประกอบที่ให้ไว้ใช้เป็นจุดยึดเท่านั้น ไม่เหมือนกับ Vue 1.x องค์ประกอบที่ติดตั้งจะถูกแทนที่ด้วย DOM ที่สร้างโดย Vue ในทุกกรณี ดังนั้นจึงไม่แนะนำให้ติดตั้ง root ไว้ที่ `<html>` หรือ `<body>`.</p>

  <p class="tip">ถ้าไม่มี `render` หรือ ฟังก์ชัน `template` มีอยู่แล้ว HTML ใน DOM ขององค์ประกอบ DOM ที่ยึดจะถูกดึงออกเป็นเทมเพลต ในกรณีนี้ควรใช้การสร้าง Runtime + Compiler ของ Vue</p>

- **เพิ่มเติม:**
  - [Lifecycle Diagram](../guide/instance.html#Lifecycle-Diagram)
  - [Runtime + Compiler vs. Runtime-only](../guide/installation.html#Runtime-Compiler-vs-Runtime-only)

### เทมเพลต

- **ประเภท:** `string`

- **รายละเอียด:**

  เทมเพลตสตริงที่จะใช้เป็นมาร์กอัปสำหรับอินสแตนซ์ Vue เทมเพลตจะ **แทนที่** องค์ประกอบที่ติดตั้ง มาร์กอัพที่มีอยู่ภายในองค์ประกอบที่ติดตั้งจะถูกละเว้นเว้นแต่ช่องการจัดจำหน่ายเนื้อหาจะมีอยู่ในเทมเพลต

  ถ้าสตริงเริ่มด้วย `#` จะใช้เป็น querySelector และใช้ innerHTML ของ element ที่เลือกเป็นสตริงเทมเพลต ซึ่งจะช่วยให้สามารถใช้ `<script type="x-template">` เพื่อรวมเทมเพลต

  <p class="tip">จากมุมมองด้านความปลอดภัยคุณควรใช้เทมเพลต Vue ที่คุณสามารถเชื่อถือได้เท่านั้น อย่าใช้เนื้อหาที่ผู้ใช้สร้างเป็นเทมเพลตของคุณ</p>

  <p class="tip">ถ้าฟังก์ชันการแสดงผลมีอยู่ในอ็อพชัน Vue แม่แบบจะถูกละเว้น</p>

- **เพิ่มเติม:**
  - [Lifecycle Diagram](../guide/instance.html#Lifecycle-Diagram)
  - [Content Distribution with Slots](../guide/components.html#Content-Distribution-with-Slots)

### เรนเดอร์

  - **ประเภท:** `(createElement: () => VNode) => VNode`

  - **รายละเอียด:**

    ทางเลือกสำหรับเทมเพลตสตริงที่ช่วยให้คุณสามารถใช้ประโยชน์จากการใช้งาน JavaScript แบบเต็มรูปแบบได้ ฟังก์ชันการแสดงผลได้รับ `createElement` เมธอดเนื่องจากเป็นอาร์กิวเมนต์แรกที่ใช้ในการสร้าง `VNode`

    ถ้าคอมโพเนนต์เป็นคอมโพเนนต์ฟังก์ชันฟังก์ชันการแสดงผลยังได้รับอาร์กิวเมนต์พิเศษ `context`, ซึ่งจะให้การเข้าถึงข้อมูลตามบริบทเนื่องจากคอมโพเนนต์การทำงานไม่ได้ใช้อินสแตนซ์

    <p class="tip">The `render` ฟังก์ชั่นที่มีความสำคัญมากกว่าฟังก์ชั่นการแสดงผลที่รวบรวมจาก `template` ตัวเลือกหรือใน DOM HTML แม่แบบขององค์ประกอบการติดตั้งที่ระบุไว้โดยตัวเลือก `el`</p>

  - **ดูเพิ่มเติมที่:** [Render Functions](../guide/render-function.html)

### renderError

> New in 2.2.0+

  - **ประเภท:** `(createElement: () => VNode, error: Error) => VNode`

  - **รายละเอียด:**

    **ทำงานได้เฉพาะในโหมดการพัฒนา**

    ให้ผลลัพธ์การแสดงผลทางเลือกเมื่อ `render` ฟังก์ชันดีฟอลต์พบข้อผิดพลาด ข้อผิดพลาดจะถูกส่งผ่านไป `renderError` เป็นอาร์กิวเมนต์ที่สอง นี้เป็นประโยชน์อย่างยิ่งเมื่อใช้ร่วมกับ hot-reload

  - **ตัวอย่าง:**

    ``` js
    new Vue({
      render (h) {
        throw new Error('oops')
      },
      renderError (h, err) {
        return h('pre', { style: { color: 'red' }}, err.stack)
      }
    }).$mount('#app')
    ```

  - **ดูเพิ่มเติมที่:** [Render Functions](../guide/render-function.html)

## Options / Lifecycle Hooks

<p class="tip">All lifecycle hooks automatically have their `this` context bound to the instance, so that you can access data, computed properties, and methods. This means __you should not use an arrow function to define a lifecycle method__ (e.g. `created: () => this.fetchTodos()`). The reason is arrow functions bind the parent context, so `this` will not be the Vue instance as you expect and `this.fetchTodos` will be undefined.</p>

### beforeCreate

- **Type:** `Function`

- **Details:**

  Called synchronously immediately after the instance has been initialized, before data observation and event/watcher setup.

- **See also:** [Lifecycle Diagram](../guide/instance.html#Lifecycle-Diagram)

### created

- **Type:** `Function`

- **Details:**

  Called synchronously after the instance is created. At this stage, the instance has finished processing the options which means the following have been set up: data observation, computed properties, methods, watch/event callbacks. However, the mounting phase has not been started, and the `$el` property will not be available yet.

- **See also:** [Lifecycle Diagram](../guide/instance.html#Lifecycle-Diagram)

### beforeMount

- **Type:** `Function`

- **Details:**

  Called right before the mounting begins: the `render` function is about to be called for the first time.

  **This hook is not called during server-side rendering.**

- **See also:** [Lifecycle Diagram](../guide/instance.html#Lifecycle-Diagram)

### mounted

- **Type:** `Function`

- **Details:**

  Called after the instance has been mounted, where `el` is replaced by the newly created `vm.$el`. If the root instance is mounted to an in-document element, `vm.$el` will also be in-document when `mounted` is called.

  Note that `mounted` does **not** guarantee that all child components have also been mounted. If you want to wait until the entire view has been rendered, you can use [vm.$nextTick](#vm-nextTick) inside of `mounted`:

  ``` js
  mounted: function () {
    this.$nextTick(function () {
      // Code that will run only after the
      // entire view has been rendered
    })
  }
  ```

  **This hook is not called during server-side rendering.**

- **See also:** [Lifecycle Diagram](../guide/instance.html#Lifecycle-Diagram)

### beforeUpdate

- **Type:** `Function`

- **Details:**

  Called when data changes, before the DOM is patched. This is a good place to access the existing DOM before an update, e.g. to remove manually added event listeners.

  **This hook is not called during server-side rendering, because only the initial render is performed server-side.**

- **See also:** [Lifecycle Diagram](../guide/instance.html#Lifecycle-Diagram)

### updated

- **Type:** `Function`

- **Details:**

  Called after a data change causes the virtual DOM to be re-rendered and patched.

  The component's DOM will have been updated when this hook is called, so you can perform DOM-dependent operations here. However, in most cases you should avoid changing state inside the hook. To react to state changes, it's usually better to use a [computed property](#computed) or [watcher](#watch) instead.

  Note that `updated` does **not** guarantee that all child components have also been re-rendered. If you want to wait until the entire view has been re-rendered, you can use [vm.$nextTick](#vm-nextTick) inside of `updated`:

  ``` js
  updated: function () {
    this.$nextTick(function () {
      // Code that will run only after the
      // entire view has been re-rendered
    })
  }
  ```

  **This hook is not called during server-side rendering.**

- **See also:** [Lifecycle Diagram](../guide/instance.html#Lifecycle-Diagram)

### activated

- **Type:** `Function`

- **Details:**

  Called when a kept-alive component is activated.

  **This hook is not called during server-side rendering.**

- **See also:**
  - [Built-in Components - keep-alive](#keep-alive)
  - [Dynamic Components - keep-alive](../guide/components.html#keep-alive)

### deactivated

- **Type:** `Function`

- **Details:**

  Called when a kept-alive component is deactivated.

  **This hook is not called during server-side rendering.**

- **See also:**
  - [Built-in Components - keep-alive](#keep-alive)
  - [Dynamic Components - keep-alive](../guide/components.html#keep-alive)

### beforeDestroy

- **Type:** `Function`

- **Details:**

  Called right before a Vue instance is destroyed. At this stage the instance is still fully functional.

  **This hook is not called during server-side rendering.**

- **See also:** [Lifecycle Diagram](../guide/instance.html#Lifecycle-Diagram)

### destroyed

- **Type:** `Function`

- **Details:**

  Called after a Vue instance has been destroyed. When this hook is called, all directives of the Vue instance have been unbound, all event listeners have been removed, and all child Vue instances have also been destroyed.

  **This hook is not called during server-side rendering.**

- **See also:** [Lifecycle Diagram](../guide/instance.html#Lifecycle-Diagram)

### errorCaptured

> New in 2.5.0+

- **Type:** `(err: Error, vm: Component, info: string) => ?boolean`

- **Details:**

  Called when an error from any descendent component is captured. The hook receives three arguments: the error, the component instance that triggered the error, and a string containing information on where the error was captured. The hook can return `false` to stop the error from propagating further.

  <p class="tip">You can modify component state in this hook. However, it is important to have conditionals in your template or render function that short circuits other content when an error has been captured; otherwise the component will be thrown into an infinite render loop.</p>

  **Error Propagation Rules**

  - By default, all errors are still sent to the global `config.errorHandler` if it is defined, so that these errors can still be reported to an analytics service in a single place.

  - If multiple `errorCaptured` hooks exist on a component's inheritance chain or parent chain, all of them will be invoked on the same error.

  - If the `errorCaptured` hook itself throws an error, both this error and the original captured error are sent to the global `config.errorHandler`.

  - An `errorCaptured` hook can return `false` to prevent the error from propagating further. This is essentially saying "this error has been handled and should be ignored." It will prevent any additional `errorCaptured` hooks or the global `config.errorHandler` from being invoked for this error.

## Options / Assets

### directives

- **Type:** `Object`

- **Details:**

  A hash of directives to be made available to the Vue instance.

- **See also:** [Custom Directives](../guide/custom-directive.html)

### filters

- **Type:** `Object`

- **Details:**

  A hash of filters to be made available to the Vue instance.

- **See also:** [`Vue.filter`](#Vue-filter)

### components

- **Type:** `Object`

- **Details:**

  A hash of components to be made available to the Vue instance.

- **See also:** [Components](../guide/components.html)

## Options / Composition

### parent

- **Type:** `Vue instance`

- **Details:**

  Specify the parent instance for the instance to be created. Establishes a parent-child relationship between the two. The parent will be accessible as `this.$parent` for the child, and the child will be pushed into the parent's `$children` array.

  <p class="tip">Use `$parent` and `$children` sparingly - they mostly serve as an escape-hatch. Prefer using props and events for parent-child communication.</p>

### mixins

- **Type:** `Array<Object>`

- **Details:**

  The `mixins` option accepts an array of mixin objects. These mixin objects can contain instance options like normal instance objects, and they will be merged against the eventual options using the same option merging logic in `Vue.extend()`. e.g. If your mixin contains a created hook and the component itself also has one, both functions will be called.

  Mixin hooks are called in the order they are provided, and called before the component's own hooks.

- **Example:**

  ``` js
  var mixin = {
    created: function () { console.log(1) }
  }
  var vm = new Vue({
    created: function () { console.log(2) },
    mixins: [mixin]
  })
  // => 1
  // => 2
  ```

- **See also:** [Mixins](../guide/mixins.html)

### extends

- **Type:** `Object | Function`

- **Details:**

  Allows declaratively extending another component (could be either a plain options object or a constructor) without having to use `Vue.extend`. This is primarily intended to make it easier to extend between single file components.

  This is similar to `mixins`.

- **Example:**

  ``` js
  var CompA = { ... }

  // extend CompA without having to call `Vue.extend` on either
  var CompB = {
    extends: CompA,
    ...
  }
  ```

### provide / inject

> New in 2.2.0+

- **Type:**
  - **provide:** `Object | () => Object`
  - **inject:** `Array<string> | { [key: string]: string | Symbol | Object }`

- **Details:**

  <p class="tip">`provide` and `inject` are primarily provided for advanced plugin / component library use cases. It is NOT recommended to use them in generic application code.</p>

  This pair of options are used together to allow an ancestor component to serve as a dependency injector for all its descendants, regardless of how deep the component hierarchy is, as long as they are in the same parent chain. If you are familiar with React, this is very similar to React's context feature.

  The `provide` option should be an object or a function that returns an object. This object contains the properties that are available for injection into its descendants. You can use ES2015 Symbols as keys in this object, but only in environments that natively support `Symbol` and `Reflect.ownKeys`.

  The `inject` option should be either:
  - an array of strings, or
  - an object where the keys are the local binding name and the value is either:
    - the key (string or Symbol) to search for in available injections, or
    - an object where:
      - the `from` property is the key (string or Symbol) to search for in available injections, and
      - the `default` property is used as fallback value

  > Note: the `provide` and `inject` bindings are NOT reactive. This is intentional. However, if you pass down an observed object, properties on that object do remain reactive.

- **Example:**

  ``` js
  // parent component providing 'foo'
  var Provider = {
    provide: {
      foo: 'bar'
    },
    // ...
  }

  // child component injecting 'foo'
  var Child = {
    inject: ['foo'],
    created () {
      console.log(this.foo) // => "bar"
    }
    // ...
  }
  ```

  With ES2015 Symbols, function `provide` and object `inject`:
  ``` js
  const s = Symbol()

  const Provider = {
    provide () {
      return {
        [s]: 'foo'
      }
    }
  }

  const Child = {
    inject: { s },
    // ...
  }
  ```

  > The next 2 examples work with Vue 2.2.1+. Below that version, injected values were resolved after the `props` and the `data` initialization.

  Using an injected value as the default for a prop:
  ```js
  const Child = {
    inject: ['foo'],
    props: {
      bar: {
        default () {
          return this.foo
        }
      }
    }
  }
  ```

  Using an injected value as data entry:
  ```js
  const Child = {
    inject: ['foo'],
    data () {
      return {
        bar: this.foo
      }
    }
  }
  ```

  > In 2.5.0+ injections can be optional with default value:

  ``` js
  const Child = {
    inject: {
      foo: { default: 'foo' }
    }
  }
  ```

  If it needs to be injected from a property with a different name, use `from` to denote the source property:

  ``` js
  const Child = {
    inject: {
      foo: {
        from: 'bar',
        default: 'foo'
      }
    }
  }
  ```

  Similar to prop defaults, you need to use a factory function for non primitive values:

  ``` js
  const Child = {
    inject: {
      foo: {
        from: 'bar',
        default: () => [1, 2, 3]
      }
    }
  }
  ```

## Options / Misc

### name

- **Type:** `string`

- **Restriction:** only respected when used as a component option.

- **Details:**

  Allow the component to recursively invoke itself in its template. Note that when a component is registered globally with `Vue.component()`, the global ID is automatically set as its name.

  Another benefit of specifying a `name` option is debugging. Named components result in more helpful warning messages. Also, when inspecting an app in the [vue-devtools](https://github.com/vuejs/vue-devtools), unnamed components will show up as `<AnonymousComponent>`, which isn't very informative. By providing the `name` option, you will get a much more informative component tree.

### delimiters

- **Type:** `Array<string>`

- **Default:** `{% raw %}["{{", "}}"]{% endraw %}`

- **Restrictions:** This option is only available in the full build, with in-browser compilation.

- **Details:**

  Change the plain text interpolation delimiters.

- **Example:**

  ``` js
  new Vue({
    delimiters: ['${', '}']
  })

  // Delimiters changed to ES6 template string style
  ```

### functional

- **Type:** `boolean`

- **Details:**

  Causes a component to be stateless (no `data`) and instanceless (no `this` context). They are only a `render` function that returns virtual nodes making them much cheaper to render.

- **See also:** [Functional Components](../guide/render-function.html#Functional-Components)

### model

> New in 2.2.0

- **Type:** `{ prop?: string, event?: string }`

- **Details:**

  Allows a custom component to customize the prop and event used when it's used with `v-model`. By default, `v-model` on a component uses `value` as the prop and `input` as the event, but some input types such as checkboxes and radio buttons may want to use the `value` prop for a different purpose. Using the `model` option can avoid the conflict in such cases.

- **Example:**

  ``` js
  Vue.component('my-checkbox', {
    model: {
      prop: 'checked',
      event: 'change'
    },
    props: {
      // this allows using the `value` prop for a different purpose
      value: String,
      // use `checked` as the prop which take the place of `value`
      checked: {
        type: Number,
        default: 0
      }
    },
    // ...
  })
  ```

  ``` html
  <my-checkbox v-model="foo" value="some value"></my-checkbox>
  ```

  The above will be equivalent to:

  ``` html
  <my-checkbox
    :checked="foo"
    @change="val => { foo = val }"
    value="some value">
  </my-checkbox>
  ```

### inheritAttrs

> New in 2.4.0+

- **Type:** `boolean`

- **Default:** `true`

- **Details:**

  By default, parent scope attribute bindings that are not recognized as props will "fallthrough" and be applied to the root element of the child component as normal HTML attributes. When authoring a component that wraps a target element or another component, this may not always be the desired behavior. By setting `inheritAttrs` to `false`, this default behavior can be disabled. The attributes are available via the `$attrs` instance property (also new in 2.4) and can be explicitly bound to a non-root element using `v-bind`.

  Note: this option does **not** affect `class` and `style` bindings.

### comments

> New in 2.4.0+

- **Type:** `boolean`

- **Default:** `false`

- **Restrictions:** This option is only available in the full build, with in-browser compilation.

- **Details:**

  When set to `true`, will preserve and render HTML comments found in templates. The default behavior is discarding them.

## Instance Properties

### vm.$data

- **Type:** `Object`

- **Details:**

  The data object that the Vue instance is observing. The Vue instance proxies access to the properties on its data object.

- **See also:** [Options / Data - data](#data)

### vm.$props

> New in 2.2.0+

- **Type:** `Object`

- **Details:**

  An object representing the current props a component has received. The Vue instance proxies access to the properties on its props object.

### vm.$el

- **Type:** `HTMLElement`

- **Read only**

- **Details:**

  The root DOM element that the Vue instance is managing.

### vm.$options

- **Type:** `Object`

- **Read only**

- **Details:**

  The instantiation options used for the current Vue instance. This is useful when you want to include custom properties in the options:

  ``` js
  new Vue({
    customOption: 'foo',
    created: function () {
      console.log(this.$options.customOption) // => 'foo'
    }
  })
  ```

### vm.$parent

- **Type:** `Vue instance`

- **Read only**

- **Details:**

  The parent instance, if the current instance has one.

### vm.$root

- **Type:** `Vue instance`

- **Read only**

- **Details:**

  The root Vue instance of the current component tree. If the current instance has no parents this value will be itself.

### vm.$children

- **Type:** `Array<Vue instance>`

- **Read only**

- **Details:**

  The direct child components of the current instance. **Note there's no order guarantee for `$children`, and it is not reactive.** If you find yourself trying to use `$children` for data binding, consider using an Array and `v-for` to generate child components, and use the Array as the source of truth.

### vm.$slots

- **Type:** `{ [name: string]: ?Array<VNode> }`

- **Read only**

- **Details:**

  Used to programmatically access content [distributed by slots](../guide/components.html#Content-Distribution-with-Slots). Each [named slot](../guide/components.html#Named-Slots) has its own corresponding property (e.g. the contents of `slot="foo"` will be found at `vm.$slots.foo`). The `default` property contains any nodes not included in a named slot.

  Accessing `vm.$slots` is most useful when writing a component with a [render function](../guide/render-function.html).

- **Example:**

  ```html
  <blog-post>
    <h1 slot="header">
      About Me
    </h1>

    <p>Here's some page content, which will be included in vm.$slots.default, because it's not inside a named slot.</p>

    <p slot="footer">
      Copyright 2016 Evan You
    </p>

    <p>If I have some content down here, it will also be included in vm.$slots.default.</p>.
  </blog-post>
  ```

  ```js
  Vue.component('blog-post', {
    render: function (createElement) {
      var header = this.$slots.header
      var body   = this.$slots.default
      var footer = this.$slots.footer
      return createElement('div', [
        createElement('header', header),
        createElement('main', body),
        createElement('footer', footer)
      ])
    }
  })
  ```

- **See also:**
  - [`<slot>` Component](#slot-1)
  - [Content Distribution with Slots](../guide/components.html#Content-Distribution-with-Slots)
  - [Render Functions - Slots](../guide/render-function.html#Slots)

### vm.$scopedSlots

> New in 2.1.0+

- **Type:** `{ [name: string]: props => VNode | Array<VNode> }`

- **Read only**

- **Details:**

  Used to programmatically access [scoped slots](../guide/components.html#Scoped-Slots). For each slot, including the `default` one, the object contains a corresponding function that returns VNodes.

  Accessing `vm.$scopedSlots` is most useful when writing a component with a [render function](../guide/render-function.html).

- **See also:**
  - [`<slot>` Component](#slot-1)
  - [Scoped Slots](../guide/components.html#Scoped-Slots)
  - [Render Functions - Slots](../guide/render-function.html#Slots)

### vm.$refs

- **Type:** `Object`

- **Read only**

- **Details:**

  An object of DOM elements and component instances, registered with [`ref` attributes](#ref).

- **See also:**
  - [Child Component Refs](../guide/components.html#Child-Component-Refs)
  - [Special Attributes - ref](#ref)

### vm.$isServer

- **Type:** `boolean`

- **Read only**

- **Details:**

  Whether the current Vue instance is running on the server.

- **See also:** [Server-Side Rendering](../guide/ssr.html)

### vm.$attrs

- **Type:** `{ [key: string]: string }`

- **Read only**

- **Details:**

  Contains parent-scope attribute bindings (except for `class` and `style`) that are not recognized (and extracted) as props. When a component doesn't have any declared props, this essentially contains all parent-scope bindings (except for `class` and `style`), and can be passed down to an inner component via `v-bind="$attrs"` - useful when creating higher-order components.

### vm.$listeners

- **Type:** `{ [key: string]: Function | Array<Function> }`

- **Read only**

- **Details:**

  Contains parent-scope `v-on` event listeners (without `.native` modifiers). This can be passed down to an inner component via `v-on="$listeners"` - useful when creating transparent wrapper components.

## Instance Methods / Data

### vm.$watch( expOrFn, callback, [options] )

- **Arguments:**
  - `{string | Function} expOrFn`
  - `{Function | Object} callback`
  - `{Object} [options]`
    - `{boolean} deep`
    - `{boolean} immediate`

- **Returns:** `{Function} unwatch`

- **Usage:**

  Watch an expression or a computed function on the Vue instance for changes. The callback gets called with the new value and the old value. The expression only accepts dot-delimited paths. For more complex expressions, use a function instead.

<p class="tip">Note: when mutating (rather than replacing) an Object or an Array, the old value will be the same as new value because they reference the same Object/Array. Vue doesn't keep a copy of the pre-mutate value.</p>

- **Example:**

  ``` js
  // keypath
  vm.$watch('a.b.c', function (newVal, oldVal) {
    // do something
  })

  // function
  vm.$watch(
    function () {
      return this.a + this.b
    },
    function (newVal, oldVal) {
      // do something
    }
  )
  ```

  `vm.$watch` returns an unwatch function that stops firing the callback:

  ``` js
  var unwatch = vm.$watch('a', cb)
  // later, teardown the watcher
  unwatch()
  ```

- **Option: deep**

  To also detect nested value changes inside Objects, you need to pass in `deep: true` in the options argument. Note that you don't need to do so to listen for Array mutations.

  ``` js
  vm.$watch('someObject', callback, {
    deep: true
  })
  vm.someObject.nestedValue = 123
  // callback is fired
  ```

- **Option: immediate**

  Passing in `immediate: true` in the option will trigger the callback immediately with the current value of the expression:

  ``` js
  vm.$watch('a', callback, {
    immediate: true
  })
  // `callback` is fired immediately with current value of `a`
  ```

### vm.$set( target, key, value )

- **Arguments:**
  - `{Object | Array} target`
  - `{string | number} key`
  - `{any} value`

- **Returns:** the set value.

- **Usage:**

  This is the **alias** of the global `Vue.set`.

- **See also:** [Vue.set](#Vue-set)

### vm.$delete( target, key )

- **Arguments:**
  - `{Object | Array} target`
  - `{string | number} key`

- **Usage:**

  This is the **alias** of the global `Vue.delete`.

- **See also:** [Vue.delete](#Vue-delete)

## Instance Methods / Events

### vm.$on( event, callback )

- **Arguments:**
  - `{string | Array<string>} event` (array only supported in 2.2.0+)
  - `{Function} callback`

- **Usage:**

  Listen for a custom event on the current vm. Events can be triggered by `vm.$emit`. The callback will receive all the additional arguments passed into these event-triggering methods.

- **Example:**

  ``` js
  vm.$on('test', function (msg) {
    console.log(msg)
  })
  vm.$emit('test', 'hi')
  // => "hi"
  ```

### vm.$once( event, callback )

- **Arguments:**
  - `{string} event`
  - `{Function} callback`

- **Usage:**

  Listen for a custom event, but only once. The listener will be removed once it triggers for the first time.

### vm.$off( [event, callback] )

- **Arguments:**
  - `{string | Array<string>} event` (array only supported in 2.2.2+)
  - `{Function} [callback]`

- **Usage:**

  Remove custom event listener(s).

  - If no arguments are provided, remove all event listeners;

  - If only the event is provided, remove all listeners for that event;

  - If both event and callback are given, remove the listener for that specific callback only.

### vm.$emit( eventName, [...args] )

- **Arguments:**
  - `{string} eventName`
  - `[...args]`

  Trigger an event on the current instance. Any additional arguments will be passed into the listener's callback function.

- **Examples:**

  Using `$emit` with only an event name:

  ```js
  Vue.component('welcome-button', {
    template: `
      <button v-on:click="$emit('welcome')">
        Click me to be welcomed
      </button>
    `
  })
  ```
  ```html
  <div id="emit-example-simple">
    <welcome-button v-on:welcome="sayHi"></welcome-button>
  </div>
  ```
  ```js
  new Vue({
    el: '#emit-example-simple',
    methods: {
      sayHi: function () {
        alert('Hi!')
      }
    }
  })
  ```
  {% raw %}
  <div id="emit-example-simple" class="demo">
    <welcome-button v-on:welcome="sayHi"></welcome-button>
  </div>
  <script>
    Vue.component('welcome-button', {
      template: `
        <button v-on:click="$emit('welcome')">
          Click me to be welcomed
        </button>
      `
    })
    new Vue({
      el: '#emit-example-simple',
      methods: {
        sayHi: function () {
          alert('Hi!')
        }
      }
    })
  </script>
  {% endraw %}

  Using `$emit` with additional arguments:

  ```js
  Vue.component('magic-eight-ball', {
    data: function () {
      return {
        possibleAdvice: ['Yes', 'No', 'Maybe']
      }
    },
    methods: {
      giveAdvice: function () {
        var randomAdviceIndex = Math.floor(Math.random() * this.possibleAdvice.length)
        this.$emit('give-advice', this.possibleAdvice[randomAdviceIndex])
      }
    },
    template: `
      <button v-on:click="giveAdvice">
        Click me for advice
      </button>
    `
  })
  ```

  ```html
  <div id="emit-example-argument">
    <magic-eight-ball v-on:give-advice="showAdvice"></magic-eight-ball>
  </div>
  ```

  ```js
  new Vue({
    el: '#emit-example-argument',
    methods: {
      showAdvice: function (advice) {
        alert(advice)
      }
    }
  })
  ```

  {% raw %}
  <div id="emit-example-argument" class="demo">
    <magic-eight-ball v-on:give-advice="showAdvice"></magic-eight-ball>
  </div>
  <script>
    Vue.component('magic-eight-ball', {
      data: function () {
        return {
          possibleAdvice: ['Yes', 'No', 'Maybe']
        }
      },
      methods: {
        giveAdvice: function () {
          var randomAdviceIndex = Math.floor(Math.random() * this.possibleAdvice.length)
          this.$emit('give-advice', this.possibleAdvice[randomAdviceIndex])
        }
      },
      template: `
        <button v-on:click="giveAdvice">
          Click me for advice
        </button>
      `
    })
    new Vue({
      el: '#emit-example-argument',
      methods: {
        showAdvice: function (advice) {
          alert(advice)
        }
      }
    })
  </script>
  {% endraw %}

## Instance Methods / Lifecycle

### vm.$mount( [elementOrSelector] )

- **Arguments:**
  - `{Element | string} [elementOrSelector]`
  - `{boolean} [hydrating]`

- **Returns:** `vm` - the instance itself

- **Usage:**

  If a Vue instance didn't receive the `el` option at instantiation, it will be in "unmounted" state, without an associated DOM element. `vm.$mount()` can be used to manually start the mounting of an unmounted Vue instance.

  If `elementOrSelector` argument is not provided, the template will be rendered as an off-document element, and you will have to use native DOM API to insert it into the document yourself.

  The method returns the instance itself so you can chain other instance methods after it.

- **Example:**

  ``` js
  var MyComponent = Vue.extend({
    template: '<div>Hello!</div>'
  })

  // create and mount to #app (will replace #app)
  new MyComponent().$mount('#app')

  // the above is the same as:
  new MyComponent({ el: '#app' })

  // or, render off-document and append afterwards:
  var component = new MyComponent().$mount()
  document.getElementById('app').appendChild(component.$el)
  ```

- **See also:**
  - [Lifecycle Diagram](../guide/instance.html#Lifecycle-Diagram)
  - [Server-Side Rendering](../guide/ssr.html)

### vm.$forceUpdate()

- **Usage:**

  Force the Vue instance to re-render. Note it does not affect all child components, only the instance itself and child components with inserted slot content.

### vm.$nextTick( [callback] )

- **Arguments:**
  - `{Function} [callback]`

- **Usage:**

  Defer the callback to be executed after the next DOM update cycle. Use it immediately after you've changed some data to wait for the DOM update. This is the same as the global `Vue.nextTick`, except that the callback's `this` context is automatically bound to the instance calling this method.

  > New in 2.1.0+: returns a Promise if no callback is provided and Promise is supported in the execution environment. Please note that Vue does not come with a Promise polyfill, so if you target browsers that don't support Promises natively (looking at you, IE), you will have to provide a polyfill yourself.

- **Example:**

  ``` js
  new Vue({
    // ...
    methods: {
      // ...
      example: function () {
        // modify data
        this.message = 'changed'
        // DOM is not updated yet
        this.$nextTick(function () {
          // DOM is now updated
          // `this` is bound to the current instance
          this.doSomethingElse()
        })
      }
    }
  })
  ```

- **See also:**
  - [Vue.nextTick](#Vue-nextTick)
  - [Async Update Queue](../guide/reactivity.html#Async-Update-Queue)

### vm.$destroy()

- **Usage:**

  Completely destroy a vm. Clean up its connections with other existing vms, unbind all its directives, turn off all event listeners.

  Triggers the `beforeDestroy` and `destroyed` hooks.

  <p class="tip">In normal use cases you shouldn't have to call this method yourself. Prefer controlling the lifecycle of child components in a data-driven fashion using `v-if` and `v-for`.</p>

- **See also:** [Lifecycle Diagram](../guide/instance.html#Lifecycle-Diagram)

## Directives

### v-text

- **Expects:** `string`

- **Details:**

  Updates the element's `textContent`. If you need to update the part of `textContent`, you should use `{% raw %}{{ Mustache }}{% endraw %}` interpolations.

- **Example:**

  ```html
  <span v-text="msg"></span>
  <!-- same as -->
  <span>{{msg}}</span>
  ```

- **See also:** [Data Binding Syntax - Interpolations](../guide/syntax.html#Text)

### v-html

- **Expects:** `string`

- **Details:**

  Updates the element's `innerHTML`. **Note that the contents are inserted as plain HTML - they will not be compiled as Vue templates**. If you find yourself trying to compose templates using `v-html`, try to rethink the solution by using components instead.

  <p class="tip">Dynamically rendering arbitrary HTML on your website can be very dangerous because it can easily lead to [XSS attacks](https://en.wikipedia.org/wiki/Cross-site_scripting). Only use `v-html` on trusted content and **never** on user-provided content.</p>

  <p class="tip">In [single-file components](../guide/single-file-components.html), `scoped` styles will not apply to content inside `v-html`, because that HTML is not processed by Vue's template compiler. If you want to target `v-html` content with scoped CSS, you can instead use [CSS modules](https://vue-loader.vuejs.org/en/features/css-modules.html) or an additional, global `<style>` element with a manual scoping strategy such as BEM.</p>

- **Example:**

  ```html
  <div v-html="html"></div>
  ```

- **See also:** [Data Binding Syntax - Interpolations](../guide/syntax.html#Raw-HTML)

### v-show

- **Expects:** `any`

- **Usage:**

  Toggles the element's `display` CSS property based on the truthy-ness of the expression value.

  This directive triggers transitions when its condition changes.

- **See also:** [Conditional Rendering - v-show](../guide/conditional.html#v-show)

### v-if

- **Expects:** `any`

- **Usage:**

  Conditionally render the element based on the truthy-ness of the expression value. The element and its contained directives / components are destroyed and re-constructed during toggles. If the element is a `<template>` element, its content will be extracted as the conditional block.

  This directive triggers transitions when its condition changes.

  <p class="tip">When used together with v-if, v-for has a higher priority than v-if. See the <a href="../guide/list.html#v-for-with-v-if">list rendering guide</a> for details.</p>

- **See also:** [Conditional Rendering - v-if](../guide/conditional.html)

### v-else

- **Does not expect expression**

- **Restriction:** previous sibling element must have `v-if` or `v-else-if`.

- **Usage:**

  Denote the "else block" for `v-if` or a `v-if`/`v-else-if` chain.

  ```html
  <div v-if="Math.random() > 0.5">
    Now you see me
  </div>
  <div v-else>
    Now you don't
  </div>
  ```

- **See also:** [Conditional Rendering - v-else](../guide/conditional.html#v-else)

### v-else-if

> New in 2.1.0+

- **Expects:** `any`

- **Restriction:** previous sibling element must have `v-if` or `v-else-if`.

- **Usage:**

  Denote the "else if block" for `v-if`. Can be chained.

  ```html
  <div v-if="type === 'A'">
    A
  </div>
  <div v-else-if="type === 'B'">
    B
  </div>
  <div v-else-if="type === 'C'">
    C
  </div>
  <div v-else>
    Not A/B/C
  </div>
  ```

- **See also:** [Conditional Rendering - v-else-if](../guide/conditional.html#v-else-if)

### v-for

- **Expects:** `Array | Object | number | string`

- **Usage:**

  Render the element or template block multiple times based on the source data. The directive's value must use the special syntax `alias in expression` to provide an alias for the current element being iterated on:

  ``` html
  <div v-for="item in items">
    {{ item.text }}
  </div>
  ```

  Alternatively, you can also specify an alias for the index (or the key if used on an Object):

  ``` html
  <div v-for="(item, index) in items"></div>
  <div v-for="(val, key) in object"></div>
  <div v-for="(val, key, index) in object"></div>
  ```

  The default behavior of `v-for` will try to patch the elements in-place without moving them. To force it to reorder elements, you need to provide an ordering hint with the `key` special attribute:

  ``` html
  <div v-for="item in items" :key="item.id">
    {{ item.text }}
  </div>
  ```

  <p class="tip">When used together with v-if, v-for has a higher priority than v-if. See the <a href="../guide/list.html#v-for-with-v-if">list rendering guide</a> for details.</p>

  The detailed usage for `v-for` is explained in the guide section linked below.

- **See also:**
  - [List Rendering](../guide/list.html)
  - [key](../guide/list.html#key)

### v-on

- **Shorthand:** `@`

- **Expects:** `Function | Inline Statement | Object`

- **Argument:** `event`

- **Modifiers:**
  - `.stop` - call `event.stopPropagation()`.
  - `.prevent` - call `event.preventDefault()`.
  - `.capture` - add event listener in capture mode.
  - `.self` - only trigger handler if event was dispatched from this element.
  - `.{keyCode | keyAlias}` - only trigger handler on certain keys.
  - `.native` - listen for a native event on the root element of component.
  - `.once` - trigger handler at most once.
  - `.left` - (2.2.0+) only trigger handler for left button mouse events.
  - `.right` - (2.2.0+) only trigger handler for right button mouse events.
  - `.middle` - (2.2.0+) only trigger handler for middle button mouse events.
  - `.passive` - (2.3.0+) attaches a DOM event with `{ passive: true }`.

- **Usage:**

  Attaches an event listener to the element. The event type is denoted by the argument. The expression can be a method name, an inline statement, or omitted if there are modifiers present.

  When used on a normal element, it listens to [**native DOM events**](https://developer.mozilla.org/en-US/docs/Web/Events) only. When used on a custom element component, it listens to **custom events** emitted on that child component.

  When listening to native DOM events, the method receives the native event as the only argument. If using inline statement, the statement has access to the special `$event` property: `v-on:click="handle('ok', $event)"`.

  Starting in 2.4.0+, `v-on` also supports binding to an object of event/listener pairs without an argument. Note when using the object syntax, it does not support any modifiers.

- **Example:**

  ```html
  <!-- method handler -->
  <button v-on:click="doThis"></button>

  <!-- inline statement -->
  <button v-on:click="doThat('hello', $event)"></button>

  <!-- shorthand -->
  <button @click="doThis"></button>

  <!-- stop propagation -->
  <button @click.stop="doThis"></button>

  <!-- prevent default -->
  <button @click.prevent="doThis"></button>

  <!-- prevent default without expression -->
  <form @submit.prevent></form>

  <!-- chain modifiers -->
  <button @click.stop.prevent="doThis"></button>

  <!-- key modifier using keyAlias -->
  <input @keyup.enter="onEnter">

  <!-- key modifier using keyCode -->
  <input @keyup.13="onEnter">

  <!-- the click event will be triggered at most once -->
  <button v-on:click.once="doThis"></button>

  <!-- object syntax (2.4.0+) -->
  <button v-on="{ mousedown: doThis, mouseup: doThat }"></button>
  ```

  Listening to custom events on a child component (the handler is called when "my-event" is emitted on the child):

  ```html
  <my-component @my-event="handleThis"></my-component>

  <!-- inline statement -->
  <my-component @my-event="handleThis(123, $event)"></my-component>

  <!-- native event on component -->
  <my-component @click.native="onClick"></my-component>
  ```

- **See also:**
  - [Event Handling](../guide/events.html)
  - [Components - Custom Events](../guide/components.html#Custom-Events)

### v-bind

- **Shorthand:** `:`

- **Expects:** `any (with argument) | Object (without argument)`

- **Argument:** `attrOrProp (optional)`

- **Modifiers:**
  - `.prop` - Bind as a DOM property instead of an attribute ([what's the difference?](https://stackoverflow.com/questions/6003819/properties-and-attributes-in-html#answer-6004028)). If the tag is a component then `.prop` will set the property on the component's `$el`.
  - `.camel` - (2.1.0+) transform the kebab-case attribute name into camelCase.
  - `.sync` - (2.3.0+) a syntax sugar that expands into a `v-on` handler for updating the bound value.

- **Usage:**

  Dynamically bind one or more attributes, or a component prop to an expression.

  When used to bind the `class` or `style` attribute, it supports additional value types such as Array or Objects. See linked guide section below for more details.

  When used for prop binding, the prop must be properly declared in the child component.

  When used without an argument, can be used to bind an object containing attribute name-value pairs. Note in this mode `class` and `style` does not support Array or Objects.

- **Example:**

  ```html
  <!-- bind an attribute -->
  <img v-bind:src="imageSrc">

  <!-- shorthand -->
  <img :src="imageSrc">

  <!-- with inline string concatenation -->
  <img :src="'/path/to/images/' + fileName">

  <!-- class binding -->
  <div :class="{ red: isRed }"></div>
  <div :class="[classA, classB]"></div>
  <div :class="[classA, { classB: isB, classC: isC }]">

  <!-- style binding -->
  <div :style="{ fontSize: size + 'px' }"></div>
  <div :style="[styleObjectA, styleObjectB]"></div>

  <!-- binding an object of attributes -->
  <div v-bind="{ id: someProp, 'other-attr': otherProp }"></div>

  <!-- DOM attribute binding with prop modifier -->
  <div v-bind:text-content.prop="text"></div>

  <!-- prop binding. "prop" must be declared in my-component. -->
  <my-component :prop="someThing"></my-component>

  <!-- pass down parent props in common with a child component -->
  <child-component v-bind="$props"></child-component>

  <!-- XLink -->
  <svg><a :xlink:special="foo"></a></svg>
  ```

  The `.camel` modifier allows camelizing a `v-bind` attribute name when using in-DOM templates, e.g. the SVG `viewBox` attribute:

  ``` html
  <svg :view-box.camel="viewBox"></svg>
  ```

  `.camel` is not needed if you are using string templates, or compiling with `vue-loader`/`vueify`.

- **See also:**
  - [Class and Style Bindings](../guide/class-and-style.html)
  - [Components - Props](../guide/components.html#Props)
  - [Components - `.sync` Modifier](../guide/components.html#sync-Modifier)

### v-model

- **Expects:** varies based on value of form inputs element or output of components

- **Limited to:**
  - `<input>`
  - `<select>`
  - `<textarea>`
  - components

- **Modifiers:**
  - [`.lazy`](../guide/forms.html#lazy) - listen to `change` events instead of `input`
  - [`.number`](../guide/forms.html#number) - cast input string to numbers
  - [`.trim`](../guide/forms.html#trim) - trim input

- **Usage:**

  Create a two-way binding on a form input element or a component. For detailed usage and other notes, see the Guide section linked below.

- **See also:**
  - [Form Input Bindings](../guide/forms.html)
  - [Components - Form Input Components using Custom Events](../guide/components.html#Form-Input-Components-using-Custom-Events)

### v-pre

- **Does not expect expression**

- **Usage:**

  Skip compilation for this element and all its children. You can use this for displaying raw mustache tags. Skipping large numbers of nodes with no directives on them can also speed up compilation.

- **Example:**

  ```html
  <span v-pre>{{ this will not be compiled }}</span>
   ```

### v-cloak

- **Does not expect expression**

- **Usage:**

  This directive will remain on the element until the associated Vue instance finishes compilation. Combined with CSS rules such as `[v-cloak] { display: none }`, this directive can be used to hide un-compiled mustache bindings until the Vue instance is ready.

- **Example:**

  ```css
  [v-cloak] {
    display: none;
  }
  ```

  ```html
  <div v-cloak>
    {{ message }}
  </div>
  ```

  The `<div>` will not be visible until the compilation is done.

### v-once

- **Does not expect expression**

- **Details:**

  Render the element and component **once** only. On subsequent re-renders, the element/component and all its children will be treated as static content and skipped. This can be used to optimize update performance.

  ```html
  <!-- single element -->
  <span v-once>This will never change: {{msg}}</span>
  <!-- the element have children -->
  <div v-once>
    <h1>comment</h1>
    <p>{{msg}}</p>
  </div>
  <!-- component -->
  <my-component v-once :comment="msg"></my-component>
  <!-- `v-for` directive -->
  <ul>
    <li v-for="i in list" v-once>{{i}}</li>
  </ul>
  ```

- **See also:**
  - [Data Binding Syntax - interpolations](../guide/syntax.html#Text)
  - [Components - Cheap Static Components with `v-once`](../guide/components.html#Cheap-Static-Components-with-v-once)

## Special Attributes

### key

- **Expects:** `number | string`

  The `key` special attribute is primarily used as a hint for Vue's virtual DOM algorithm to identify VNodes when diffing the new list of nodes against the old list. Without keys, Vue uses an algorithm that minimizes element movement and tries to patch/reuse elements of the same type in-place as much as possible. With keys, it will reorder elements based on the order change of keys, and elements with keys that are no longer present will always be removed/destroyed.

  Children of the same common parent must have **unique keys**. Duplicate keys will cause render errors.

  The most common use case is combined with `v-for`:

  ``` html
  <ul>
    <li v-for="item in items" :key="item.id">...</li>
  </ul>
  ```

  It can also be used to force replacement of an element/component instead of reusing it. This can be useful when you want to:

  - Properly trigger lifecycle hooks of a component
  - Trigger transitions

  For example:

  ``` html
  <transition>
    <span :key="text">{{ text }}</span>
  </transition>
  ```

  When `text` changes, the `<span>` will always be replaced instead of patched, so a transition will be triggered.

### ref

- **Expects:** `string`

  `ref` is used to register a reference to an element or a child component. The reference will be registered under the parent component's `$refs` object. If used on a plain DOM element, the reference will be that element; if used on a child component, the reference will be component instance:

  ``` html
  <!-- vm.$refs.p will be the DOM node -->
  <p ref="p">hello</p>

  <!-- vm.$refs.child will be the child component instance -->
  <child-component ref="child"></child-component>
  ```

  When used on elements/components with `v-for`, the registered reference will be an Array containing DOM nodes or component instances.

  An important note about the ref registration timing: because the refs themselves are created as a result of the render function, you cannot access them on the initial render - they don't exist yet! `$refs` is also non-reactive, therefore you should not attempt to use it in templates for data-binding.

- **See also:** [Child Component Refs](../guide/components.html#Child-Component-Refs)

### slot

- **Expects:** `string`

  Used on content inserted into child components to indicate which named slot the content belongs to.

  For detailed usage, see the guide section linked below.

- **See also:** [Named Slots](../guide/components.html#Named-Slots)

### slot-scope

> New in 2.5.0+

- **Expects:** `function argument expression`

- **Usage:**

  Used to denote an element or component as a scoped slot. The attribute's value should be a valid JavaScript expression that can appear in the argument position of a function signature. This means in supported environments you can also use ES2015 destructuring in the expression. Serves as a replacement for [`scope`](#scope-replaced) in 2.5.0+.

  This attribute does not support dynamic binding.

- **See also:** [Scoped Slots](../guide/components.html#Scoped-Slots)

### scope <sup>replaced</sup>

Used to denote a `<template>` element as a scoped slot, which is replaced by [`slot-scope`](#slot-scope) in 2.5.0+.

- **Usage:**

  Same as [`slot-scope`](#slot-scope) except that `scope` can only be used on `<template>` elements.

### is

- **Expects:** `string | Object (component’s options object)`

  Used for [dynamic components](../guide/components.html#Dynamic-Components) and to work around [limitations of in-DOM templates](../guide/components.html#DOM-Template-Parsing-Caveats).

  For example:

  ``` html
  <!-- component changes when currentView changes -->
  <component v-bind:is="currentView"></component>

  <!-- necessary because `<my-row>` would be invalid inside -->
  <!-- a `<table>` element and so would be hoisted out      -->
  <table>
    <tr is="my-row"></tr>
  </table>
  ```

  For detailed usage, follow the links in the description above.

- **See also:**
  - [Dynamic Components](../guide/components.html#Dynamic-Components)
  - [DOM Template Parsing Caveats](../guide/components.html#DOM-Template-Parsing-Caveats)

## Built-In คอมโพเนนต์

### คอมโพเนนต์

- **ข้อดี:**
  - `is` - string | ComponentDefinition | ComponentConstructor
  - `inline-template` - boolean

- **การใช้:**

  "คอมโพเนนต์ meta" สำหรับการแสดงองค์ประกอบแบบไดนามิก คอมโพเนนต์ที่แท้จริง ในการแสดงผลจะถูกกำหนดโดย `is` :

  ```html
  <!-- a dynamic component controlled by -->
  <!-- the `componentId` property on the vm -->
  <component :is="componentId"></component>

  <!-- can also render registered component or component passed as prop -->
  <component :is="$options.components.child"></component>
  ```

- **ดูเพิ่มเติมที่:** [Dynamic Components](../guide/components.html#Dynamic-Components)

### transition

- **ข้อดี:**
  - `name` - สตริงใช้เพื่อสร้างชื่อคลาส CSS ขั้นสูงโดยอัตโนมัติ เช่น `name: 'fade'` จะขยายไปยังอัตโนมัติ `.fade-enter`, `.fade-enter-active`, ฯลฯ ค่าเริ่มต้นไป `"v"`.
  - `appear` - boolean ไม่ว่าจะใช้การเปลี่ยนแปลงในการแสดงผลเริ่มต้นหรือไม่ ค่าเริ่มต้นเป็น `false`.
  - `css` - boolean ไม่ว่าจะใช้ CSS transition ค่าเริ่มต้นเป็น `true`. ถ้าตั้งไว้เป็น `false`, จะเรียกใช้ JavaScript hooks ที่ลงทะเบียนผ่านเหตุการณ์ component เท่านั้น
  - `type` - ระบุประเภทของเหตุการณ์การเปลี่ยนแปลงที่จะรอเพื่อกำหนดระยะเวลาการสิ้นสุดการเปลี่ยนแปลง ค่าที่มีอยู่คือ `"transition"` และ `"animation"`. โดยค่าเริ่มต้นระบบจะตรวจหาประเภทที่มีระยะเวลานานขึ้นโดยอัตโนมัติ
  - `mode` - สตริง, ควบคุมลำดับเวลาของการออก / เข้าสู่ช่วง โหมดที่ใช้ได้คือ`"out-in"` และ `"in-out"`; ค่าเริ่มต้นเหมือนกัน
  - `enter-class` - สตริง
  - `leave-class` - สตริง
  - `appear-class` - สตริง
  - `enter-to-class` - สตริง
  - `leave-to-class` - สตริง
  - `appear-to-class` - สตริง
  - `enter-active-class` - สตริง
  - `leave-active-class` - สตริง
  - `appear-active-class` - สตริง

- **กรณี:**
  - `before-enter`
  - `before-leave`
  - `before-appear`
  - `enter`
  - `leave`
  - `appear`
  - `after-enter`
  - `after-leave`
  - `after-appear`
  - `enter-cancelled`
  - `leave-cancelled` (`v-show` only)
  - `appear-cancelled`

- **การใช้:**

  `<transition>` ทำหน้าที่เป็นเอฟเฟ็กการเปลี่ยนแปลงสำหรับองค์ประกอบ / คอมโพเนนต์ `<transition>` ใช้เฉพาะพฤติกรรมการเปลี่ยนไปยังเนื้อหาที่ห่อภายใน ไม่แสดงองค์ประกอบ DOM แบบพิเศษ หรือแสดงในการตรวจสอบ ลำดับชั้นคอมโพเนนต์

  ```html
  <!-- องค์ประกอบที่เรียบง่าย -->
  <transition>
    <div v-if="ok">toggled content</div>
  </transition>

  <!-- คอมโพเนนต์แบบไดนามิก -->
  <transition name="fade" mode="out-in" appear>
    <component :is="view"></component>
  </transition>

  <!-- เหตุการณ์ hooking -->
  <div id="transition-demo">
    <transition @after-enter="transitionComplete">
      <div v-show="ok">toggled content</div>
    </transition>
  </div>
  ```

  ``` js
  new Vue({
    ...
    methods: {
      transitionComplete: function (el) {
        // for passed 'el' that DOM element as the argument, something ...
      }
    }
    ...
  }).$mount('#transition-demo')
  ```

- **ดูเพิ่มเติม:** [Transitions: Entering, Leaving, and Lists](../guide/transitions.html)

### การเปลี่ยนแปลงกลุ่ม

- **ข้อดี:**
  - `tag` - สตริงค่าเริ่มต้นเป็น `span`.
  - `move-class` - เขียนทับ CSS class ที่ใช้ระหว่างการย้ายการเปลี่ยนแปลง
  - ทำให้มีพร็อพเดียวกับ `<transition>` ยกเว้น `mode`.

- **เหตุการณ์:**
  - แสดงถึงเหตุการณ์เช่นเดียวกับ `<transition>`.

- **การใช้:**

  `<transition-group>` เป็นผลการเปลี่ยนแปลงสำหรับ **หลายๆ** elements/components. The `<transition-group>` แสดงองค์ประกอบ DOM จริง โดยค่าเริ่มต้นจะแสดงผล `<span>`, และคุณสามารถกำหนดค่าสิ่งที่องค์ประกอบควรแสดงผลผ่านทาง ลักษณะ `tag` 

  `<transition-group>` ต้องเป็นคีย์ที่ **ไม่ซ้ำกัน**สำหรับภาพเคลื่อนไหวในการทำงานอย่างถูกต้อง

  `<transition-group>` สนับสนุนการเปลี่ยนการเคลื่อนย้ายผ่านการแปลง CSS เมื่อตำแหน่งของเด็กบนหน้าจอมีการเปลี่ยนแปลงหลังจากอัปเดตแล้วจะมีการใช้คลาส CSS ที่กำลังเคลื่อนที่ (สร้างโดยอัตโนมัติจาก `name` หรือกำหนดค่าด้วย แอตทริบิวต์ `move-class` ). ถ้าเป็น CSS `transform` คุณสมบัติคือ "transition-able" เมื่อมีการเคลื่อนย้ายคลาสองค์ประกอบจะเคลื่อนไหวได้อย่างราบรื่นไปยังปลายทางโดยใช้ [FLIP technique](https://aerotwist.com/blog/flip-your-animations/).

  ```html
  <transition-group tag="ul" name="slide">
    <li v-for="item in items" :key="item.id">
      {{ item.text }}
    </li>
  </transition-group>
  ```

- **ดูเพิ่มเติม:** [Transitions: Entering, Leaving, and Lists](../guide/transitions.html)

### keep-alive

- **ข้อดี:**
  - `include` - สตริงหรือ RegExp หรือ Array เฉพาะคอมโพเนนต์ที่ตรงกับข้อมูลนี้จะถูกแคช
  - `exclude` - สตริงหรือ RegExp หรือ Array คอมโพเนนต์ที่ตรงกับสิ่งนี้จะไม่ถูกแคช

- **การใช้:**

  เมื่อล้อมรอบคอมโพเนนต์แบบไดนามิก `<keep-alive>` เก็บแคชอินสแตนซ์ของส่วนประกอบที่ไม่มีการใช้งานโดยไม่ทำลายองค์ประกอบเหล่านั้น คล้ายกับ `<transition>`, `<keep-alive>` เป็นคอมโพเนนต์แบบนามธรรม: มันไม่ได้ทำให้องค์ประกอบ DOM ที่ตัวเอง และไม่ปรากฏขึ้นในองค์ประกอบหลัก

  เมื่อคอมโพเนนต์ถูกสลับด้านใน `<keep-alive>`, its `activated` และ `deactivated` วงจร hooks จะถูกเรียกตาม

  > In 2.2.0+ and above, `activated` and `deactivated` will fire for all nested components inside a `<keep-alive>` tree.

  นำมาใช้เป็นหลักในการรักษาสถานะส่วนประกอบหรือหลีกเลี่ยงการแสดงผลอีกครั้ง

  ```html
  <!-- พื้นฐาน -->
  <keep-alive>
    <component :is="view"></component>
  </keep-alive>

  <!-- มีหลายเงื่อนไข -->
  <keep-alive>
    <comp-a v-if="a > 1"></comp-a>
    <comp-b v-else></comp-b>
  </keep-alive>

  <!-- ใช้ร่วมกับ `<transition>` -->
  <transition>
    <keep-alive>
      <component :is="view"></component>
    </keep-alive>
  </transition>
  ```

  Note, `<keep-alive>` ได้รับการออกแบบมาสำหรับกรณีที่มีส่วนประกอบลูกโดยตรงซึ่งกำลังมีการสลับ มันไม่ทำงานถ้าคุณมี `v-for` อยู่ภายใน เมื่อมีเด็กหลายเงื่อนไขตามที่ระบุไว้ด้านบน `<keep-alive>` ต้องการให้มีเพียงเด็กคนหนึ่งที่แสดงผลในแต่ละครั้งเท่านั้น

- **`include` และ `exclude`**

  > New in 2.1.0+

  The `include` and `exclude` props อนุญาตให้คอมโพเนนต์ถูกแคชตามเงื่อนไข อุปกรณ์ทั้งสองสามารถเป็นสตริงคั่นด้วยจุลภาค RegExp หรือ Array:

  ``` html
  <!-- คั่นด้วยเครื่องหมายจุลภาค -->
  <keep-alive include="a,b">
    <component :is="view"></component>
  </keep-alive>

  <!-- regex (use `v-bind`) -->
  <keep-alive :include="/a|b/">
    <component :is="view"></component>
  </keep-alive>

  <!-- อเรย์ (use `v-bind`) -->
  <keep-alive :include="['a', 'b']">
    <component :is="view"></component>
  </keep-alive>
  ```

  การจับคู่จะได้รับการตรวจสอบตัว `name` เลือกของตัวเองเป็นอันดับแรกจากนั้นชื่อการลงทะเบียนท้องถิ่น (คีย์ใน `components` option) ถ้า `name` ตัวเลือกไม่พร้อมใช้งาน คอมโพเนนต์ที่ไม่ระบุชื่อไม่สามารถจับคู่กับ

  <p class="tip">`<keep-alive>` ไม่ทำงานกับส่วนประกอบที่ทำงานได้เนื่องจากไม่มีอินสแตนซ์ที่จะแคช</p>

- **ดูเพิ่มเติม:** [Dynamic Components - keep-alive](../guide/components.html#keep-alive)

### สล็อต

- **ข้อดี:**
  - `name` - สตริงใช้สำหรับ named slot.

- **การใช้:**

  `<slot>` เป็นแหล่งแจกจ่ายเนื้อหาในเทมเพลตของคอมโพเนนต์  `<slot>` ตัวเองจะถูกแทนที่

  สำหรับรายละเอียดการใช้งานให้ดูที่ส่วนคู่มือด้านล่าง

- **ดูเพิ่มเติม:** [Content Distribution with Slots](../guide/components.html#Content-Distribution-with-Slots)

## VNode Interface

- โปรดดูที่ [VNode class declaration](https://github.com/vuejs/vue/blob/dev/src/core/vdom/vnode.js).

## Server-Side Rendering

- โปรดดูที่ [vue-server-renderer package documentation](https://github.com/vuejs/vue/tree/dev/packages/vue-server-renderer).
