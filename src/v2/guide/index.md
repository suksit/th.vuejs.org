---
title: บทนำ
type: guide
order: 2
---

## Vue.js คืออะไร?

Vue (อ่านว่า 'วิว' เหมือน **view** ที่แปลว่า **ทิวทัศน์**) คือ **เฟรมเวอร์คสำหรับอนาคต** สำหรับสร้างส่วนติดต่อผู้ใช้งาน (user interfaces) ที่ไม่เหมือนกับเฟรมเวอร์คอื่น ซึ่ง Vue ออกแบบมาสำหรับสร้างแอพพลิเคชันตั้งแต่เริ่มต้นและเพิ่มเติมส่วนอื่นขึ้นเรื่อยๆ โดยที่ไลบรารีหลักจะมุ่งเน้นไปที่ view layer เท่านั้น และสามารถเพิ่มส่วนอื่นเข้ามาได้ง่ายด้วยไลบรารีอื่นๆ หรือที่มีให้แล้วในโปรเจค ในทางกลับกัน Vue ยังมีความสามารถอย่างยอดเยี่ยมสำหรับเว็บแอพพลิเคชันหน้าเดียว (SPA) ที่ซับซ้อนได้ เมื่อใช้ร่วมกับ [เครื่องมือสมัยใหม่](single-file-components.html) และ [ไลบรารีสนับสนุน](https://github.com/vuejs/awesome-vue#components--libraries)

ถ้าคุณต้องการเรียนรู้เพิ่มเติมเกี่ยวกับ Vue นั้น ก่อนที่จะเริ่มต้น ทีมงานได้ <a id="modal-player"  href="#">สร้างวีดีโอ</a> สำหรับนำเสนอหลักการสำคัญและโปรเจคตัวอย่างไว้ให้ได้ชมก่อน

ถ้าคุณมีประสบการณ์พัฒนา frontend แล้ว และต้องการเปรียบเทียบระหว่าง Vue และไลบรารีหรือเฟรมเวอร์คอื่นๆ สามารดูได้ที่ [การเปรียบเทียบกับเฟรมเวอร์คอื่น](comparison.html)

## เริ่มต้นกันเลย

<p class="tip">คำแนะนำอย่างเป็นทางการนี้สร้างขึ้นโดยถือว่าคุณมีความรู้ระดับกลางสำหรับ HTML, CSS และ JavaScript ถ้าคุณใหม่มากๆ สำหรับการพัฒนา fontend คำแนะนำนี้อาจจะไม่เหมาะสมสำหรับคุณ - คุณอาจจะต้องเรียนรู้พื้นฐานก่อนแล้วกลับมาที่คำคำแนะนำนี้ใหม่! ประสบการณ์จากเฟรมเวอร์คอื่นก่อนหน้านี้อาจจะช่วยได้ แต่ก็ไม่จำเป็น</p>

วิธีที่ง่ายที่สุดที่จะลองใช้ Vue.js คือใช้ [JSFiddle ตัวอย่าง Hello World](https://jsfiddle.net/chrisvfritz/50wL7mdz/) สามารถเปิดลิงค์นี้ในหน้าต่างใหม่และลองพิจารณาส่วนต่างๆ ของโค้ดตัวอย่างเบื้องต้นที่ให้มา หรือสามารถ <a href="https://gist.githubusercontent.com/chrisvfritz/7f8d7d63000b48493c336e48b3db3e52/raw/ed60c4e5d5c6fec48b0921edaed0cb60be30e87c/index.html" target="_blank" download="index.html">สร้างไพล์ <code>index.html</code></a> ใหม่ และ include Vue ด้วย:

``` html
<!-- เวอร์ชันสำหรับพัฒนา ซึ่งจะ include console warning ที่เป็นประโยชน์ต่างๆ -->
<script src="https://cdn.jsdelivr.net/npm/vue/dist/vue.js"></script>
```

หรือ:

``` html
<!-- เวอร์ชันสำหรับโปรดักชัน ซึ่งจะปรับแต่งขนาดและความเร็วให้มีประสิทธิภาพมากที่สุด -->
<script src="https://cdn.jsdelivr.net/npm/vue"></script>
```

หน้าเพจ [การติดตั้ง](installation.html) จะให้ตัวเลือกเพิ่มเติ่มสำหรับการติดตั้ง Vue หมายเหตุ: เรา **ไม่แนะนำ** ให้ผู้เริ่มต้น กระโดดไปเริ่มกับ `vue-cli` โดยเฉพาะอย่างยิ่ง ถ้าคุณไม่ได้คุ้นเคยกับเครื่องมือของ Node.js

ถ้าคุณต้องการอะไรที่มีความอินเตอเอกทีฟ คุณสามารถตรวจสอบได้ที่ [ชุดการสอน Scrimba](https://scrimba.com/playlist/pXKqta) ซึ่งจะได้เรียนรู้จากการผสมระหว่าง วิดีโอการสอน และ ส่วนทดลองเขียนโค้ด ที่คุณสมารถหยุดและเล่นวิดีโอได้ตลอดเวลา และทดลองเขียนโค้ดได้เลย

## การประกาศการแสดงผล

<div class="scrimba"><a href="https://scrimba.com/p/pXKqta/cQ3QVcr" target="_blank">ลองบทเรียนนี้บน Scrimba</a></div>

ไลบรารีหลักของ Vue.js เป็นระบบที่อนุญาติให้เราประกาศการแสดงผลข้อมูลไปยัง DOM โดยใช้เทมเพลตอย่างตรงไปตรงมาด้วยไวยากรณ์:

``` html
<div id="app">
  {{ message }}
</div>
```
``` js
var app = new Vue({
  el: '#app',
  data: {
    message: 'Hello Vue!'
  }
})
```
{% raw %}
<div id="app" class="demo">
  {{ message }}
</div>
<script>
var app = new Vue({
  el: '#app',
  data: {
    message: 'Hello Vue!'
  }
})
</script>
{% endraw %}

จากโค้ดข้างต้น เราได้สร้างแอพพลิเคชัน Vue แรกได้แล้ว! แอพนี้ดูเหมือนว่าแสดงผลเทมเพลตข้อความธรรมดา แต่ทว่า Vue ทำหลายอย่างมากในเบื้องหลัง ข้อมูลและ ​DOM ถูกเชื่อมโยงกัน และทุกสิ่งเป็น **การตอบสอนงทันที (reactive)** เราจะรู้ได้อย่างไรล่ะมันเป็นแบบนั้นจริงๆ ลองเปิด JavaScript คอนโซลของเว็บเบราเซอร์ (ลองได้ในเพจนี้) และใส่ค่า `app.message` ให้เป็นค่าอื่น คุณจะเห็นว่าค่าของข้อความในตัวอย่างจะเปลี่ยนไปทันที

เพิ่มเติมจากการแก้ไขข้อความ เราสามารถเชื่อมโยงแอตทริบิวต์ขององค์ประกอบต่างๆ ดังนี้:

``` html
<div id="app-2">
  <span v-bind:title="message">
    Hover your mouse over me for a few seconds
    to see my dynamically bound title!
  </span>
</div>
```
``` js
var app2 = new Vue({
  el: '#app-2',
  data: {
    message: 'You loaded this page on ' + new Date().toLocaleString()
  }
})
```
{% raw %}
<div id="app-2" class="demo">
  <span v-bind:title="message">
    Hover your mouse over me for a few seconds to see my dynamically bound title!
  </span>
</div>
<script>
var app2 = new Vue({
  el: '#app-2',
  data: {
    message: 'You loaded this page on ' + new Date().toLocaleString()
  }
})
</script>
{% endraw %}

ตอนนี้ จากโค้ดด้านบนเราจะเจอคำใหม่ นั้นคือ แอตทริบิวต์ `v-bind` จะเห็นว่ามันถูกเรียกโดยตรงแบบ **ไดเรกทีฟ (directive)** ไดเรกทีฟจะนำหน้าด้วย `v-` เพื่อระบุว่าเป็นแอตทริบิวต์พิเศษของ Vue และทำให้สามารถเดาได้ แอตทริบิวต์เหลานี้ใช้ตอบสนองพิเศษเพื่อแสดงผล DOM อาจจะพูดได้ง่ายๆ ว่า "ให้อับเดตแอตทริบิวต์ขององค์ประกอบ `title` เสมอ ด้วยข้อมูล `message` บนอินสแตนส์ของ Vue

ถ้าเปิด JavaScript คอนโซลของคุณอีกครั้งและใส่คำสั่ง `app2.message = 'some new message'` จะเห็นได้ว่าข้อความที่เชื่อมโยงกับ HTML จะเปลี่ยนไป - ในกรณีนี้แอตทริบิวต์ของ `title` จะเปลี่ยนไป

## เงือนไขและการวนซ้ำ

<div class="scrimba"><a href="https://scrimba.com/p/pXKqta/cEQe4SJ" target="_blank">ลองบทเรียนนี้บน Scrimba</a></div>

มันง่ายมาก ที่จะสลับการแสดงองค์ประกอบ ด้วย:

``` html
<div id="app-3">
  <span v-if="seen">Now you see me</span>
</div>
```

``` js
var app3 = new Vue({
  el: '#app-3',
  data: {
    seen: true
  }
})
```

{% raw %}
<div id="app-3" class="demo">
  <span v-if="seen">Now you see me</span>
</div>
<script>
var app3 = new Vue({
  el: '#app-3',
  data: {
    seen: true
  }
})
</script>
{% endraw %}

ลองใส่คำสั่ง `app3.seen = false` ในคอนโซล คุณจะเห็นได้ว่าข้อความที่แสดงก่อนหน้านนี้หายไป

ในตัวอย่างนี้แสดงให้เห็นว่าเราสามารถเชื่อมโยงข้อมูลไม่เพียงแต่ข้อความและแอตทริบิวต์ แต่สามารถเชื่องโยงกับ **โครงสร้าง** ของ DOM ได้ด้วย มากไปกว่านั้น Vue ยังมีระบบผลลัพธ์การเปลี่ยนแปลงที่มีประสิทธิภาพ ซึ่งสามารใช้ [ผลลัพธ์การเปลี่ยนแปลง](transitions.html) ได้อัตโนมัติ เมื่อส่วนประกอบนั้น แทรก/ปรับปรุง/ลบออก โดย Vue

นอกจากนี้ยังมีไดเรกทีฟอื่นที่มีการทำงานพิเศษของตัวเอง ยกตัวอย่างเช่น ไดเรกทีฟ `v-for` สามารถใช้แสดงรายการของข้อมูลจากอาเรย์

``` html
<div id="app-4">
  <ol>
    <li v-for="todo in todos">
      {{ todo.text }}
    </li>
  </ol>
</div>
```
``` js
var app4 = new Vue({
  el: '#app-4',
  data: {
    todos: [
      { text: 'Learn JavaScript' },
      { text: 'Learn Vue' },
      { text: 'Build something awesome' }
    ]
  }
})
```
{% raw %}
<div id="app-4" class="demo">
  <ol>
    <li v-for="todo in todos">
      {{ todo.text }}
    </li>
  </ol>
</div>
<script>
var app4 = new Vue({
  el: '#app-4',
  data: {
    todos: [
      { text: 'Learn JavaScript' },
      { text: 'Learn Vue' },
      { text: 'Build something awesome' }
    ]
  }
})
</script>
{% endraw %}

ในคอนโซล ใสคำสั่ง `app4.todos.push({ text: 'New item' })` คุณควรจะเห็นรายการใหม่เพิ่มเข้าไปในรายการ

## จัดการกับการป้อนข้อมูลผู้ใช้

<div class="scrimba"><a href="https://scrimba.com/p/pXKqta/czPNaUr" target="_blank">ลองบทเรียนนี้บน Scrimba</a></div>

เพื่อให้ผู้ใช้มีปฏิสัมพันธ์กับแอพพลิเคชันของคุณ เราสามารภใช้ไดเรกทีฟ `v-on` เพื่อแนบ event listener ที่จะเรียกฟังก์ชันในอินสแตนส์ของ Vue

``` html
<div id="app-5">
  <p>{{ message }}</p>
  <button v-on:click="reverseMessage">Reverse Message</button>
</div>
```
``` js
var app5 = new Vue({
  el: '#app-5',
  data: {
    message: 'Hello Vue.js!'
  },
  methods: {
    reverseMessage: function () {
      this.message = this.message.split('').reverse().join('')
    }
  }
})
```
{% raw %}
<div id="app-5" class="demo">
  <p>{{ message }}</p>
  <button v-on:click="reverseMessage">Reverse Message</button>
</div>
<script>
var app5 = new Vue({
  el: '#app-5',
  data: {
    message: 'Hello Vue.js!'
  },
  methods: {
    reverseMessage: function () {
      this.message = this.message.split('').reverse().join('')
    }
  }
})
</script>
{% endraw %}

หมายเหตุว่าเมธอดนี้ เราอัพเดตสถานะของแอพพลิเคชันของเราโดยปราศจากการสัมผัส DOM - DOM ทั้งหมดจะถูกจัดการโดย Vue  และโค้ดที่คุณเขียนขึ้นมาจะเน้นที่ตรรกะพื้นฐานของแอพพลิเคชัน

โดย Vue มีไดเรกทีฟ `v-model` ที่ทำการเชื่อมโยงสองทาง (two-way binding) ระหว่างแบบฟอร์มและสถานะของแอพพลิเคชันอย่างรวดเร็ว

``` html
<div id="app-6">
  <p>{{ message }}</p>
  <input v-model="message">
</div>
```
``` js
var app6 = new Vue({
  el: '#app-6',
  data: {
    message: 'Hello Vue!'
  }
})
```
{% raw %}
<div id="app-6" class="demo">
  <p>{{ message }}</p>
  <input v-model="message">
</div>
<script>
var app6 = new Vue({
  el: '#app-6',
  data: {
    message: 'Hello Vue!'
  }
})
</script>
{% endraw %}

## การเขียนคอมโพแนนต์

<div class="scrimba"><a href="https://scrimba.com/p/pXKqta/cEQVkA3" target="_blank">ลองบทเรียนนี้บน Scrimba</a></div>

ระบบคอมโพแนนต์ เป็นอีกแนวคิดที่สำคัญของ Vue เพราะว่าเป็นส่วนนามธรรม ที่อนุญาติให้พวกเราสร้างแอพพลิเคชันขนาดใหญ่ ที่ประกอบด้วยส่วนประกอบขนาดเล็ก ไม่เกี่ยวข้องกับใคร และสามารถนำกลับมาใช้ใหม่ได้ ถ้าพวกเราคิดถึงสิ่งเหล่านี้ แทบทุกชนิดของแอพพลิเคชันอินเทอเฟสสามารถแยกออกเป็นโครงสร้างต้นไม้ของคอมโพแนนต์:

![Component Tree](/images/components.png)

ใน Vue คอมโพแนนต์เป็นส่วนสำคัญของวิวอินสแตนซ์ ด้วยตัวเลือกที่กำหนดไว้ล่วงหน้า การลงทะเบียนคอมโพแนนต์ใน Vue ทำได้โดยตรง

``` js
// Define a new component called todo-item
Vue.component('todo-item', {
  template: '<li>This is a todo</li>'
})
```

ณ ตอนนี้ คุณสามารถเรียบเรียงคอมโพแนนต์ในแบบคอมโพแนนต์อื่นได้:

``` html
<ol>
  <!-- Create an instance of the todo-item component -->
  <todo-item></todo-item>
</ol>
```

จากโค้ดข้างต้นจะแสดงข้อความเหมือนกันสำหรับทุกๆ รายการ todo ซึ่งไม่ใช่สิ่งที่เราต้องการ ดังนั้นเราควรจะส่งผ่านข้อมูลจากสโคปแม่ไปยังคอมโพแนนต์ลูก โดยแก้ไขข้อกำหนดของคอมโพแนนต์เพื่อทำให้มันรับ [prop](components.html#Props):

``` js
Vue.component('todo-item', {
  // The todo-item component now accepts a
  // "prop", which is like a custom attribute.
  // This prop is called todo.
  props: ['todo'],
  template: '<li>{{ todo.text }}</li>'
})
```

ณ ตอนนี้ เราสามารถส่งผ่านข้อมูล todo ไปยังแต่ล่ะคอมโพแนนต์โดยใช้ไดเรกทีฟ `v-bind`:

``` html
<div id="app-7">
  <ol>
    <!--
      Now we provide each todo-item with the todo object
      it's representing, so that its content can be dynamic.
      We also need to provide each component with a "key",
      which will be explained later.
    -->
    <todo-item
      v-for="item in groceryList"
      v-bind:todo="item"
      v-bind:key="item.id">
    </todo-item>
  </ol>
</div>
```
``` js
Vue.component('todo-item', {
  props: ['todo'],
  template: '<li>{{ todo.text }}</li>'
})

var app7 = new Vue({
  el: '#app-7',
  data: {
    groceryList: [
      { id: 0, text: 'Vegetables' },
      { id: 1, text: 'Cheese' },
      { id: 2, text: 'Whatever else humans are supposed to eat' }
    ]
  }
})
```
{% raw %}
<div id="app-7" class="demo">
  <ol>
    <todo-item v-for="item in groceryList" v-bind:todo="item" :key="item.id"></todo-item>
  </ol>
</div>
<script>
Vue.component('todo-item', {
  props: ['todo'],
  template: '<li>{{ todo.text }}</li>'
})
var app7 = new Vue({
  el: '#app-7',
  data: {
    groceryList: [
      { id: 0, text: 'Vegetables' },
      { id: 1, text: 'Cheese' },
      { id: 2, text: 'Whatever else humans are supposed to eat' }
    ]
  }
})
</script>
{% endraw %}

จากตัวอย่างข้างต้น เราสามารถจัดการแยกแอพพลิเคลันของเราออกเป็น 2 ส่วนเล็กๆ และคอมโพแนนต์ลูกคือส่วนที่แยกส่วนออกจากแอพพลิเคชันแม่ด้วย props อินเทอเฟส เราสามารถปรับปรุงคอมโพแนนต์ `<todo-item>` ด้วยแทมเพลตและตรรกะที่ซับซ้อนขึ้นโดยปราศจากผลกระทบกับแอพลิเคชันแม่

ในแอพพลิเคชันขนาดใหญ่จำเป็นต้องแบ่งแอพพลิเคชันออกเป็นคอมโพแนนต์เพื่อทำให้การพัฒนาสามารถจัดการได้ เราจะกล่าวเพิ่มเติมเกี่ยวกับคอมโพแนนต์[คำแนะนำในภายหลัง](components.html) โดยโครงสร้างตัวอย่างของแอพพลิเคชันแทมเพลตอาจจะประกอบด้วยคอมโพแนนต์ต่างๆ:

``` html
<div id="app">
  <app-nav></app-nav>
  <app-view>
    <app-sidebar></app-sidebar>
    <app-content></app-content>
  </app-view>
</div>
```

### ความสัมพันธ์กับองค์ประกอบที่กำหนดเอง

คุณอาจจะสังเกตเห็นว่าคอมโพแนนต์ของ Vue จะเหมือนกับ **องค์ประกอบที่กำหนดเอง** ซึ่งเป็นส่วนของ [ส่วนประกอบของเว็บ](https://www.w3.org/wiki/WebComponents/) นั้นเพราะว่าไวยกรณ์ของคอมโพแนนต์ของ Vue จำลองอย่างหลวมๆ หลังจากข้อกำหนด ตัวอย่างเช่น การพัฒนาคอมโพแนนต์ของ Vue [Slot API](https://github.com/w3c/webcomponents/blob/gh-pages/proposals/Slots-Proposal.md) และ`เป็น` แอททริบิวพิเศษ อย่างไรก็ตาม มีส่วนที่แตกต่างกันอยู่บ้างดังนี้:

1. ข้อกำหนดของเว็บคอมโพแนนต์เป็นเพียงแค่สถานะร่าง และไม่ใช้การพัฒนาโดยกำเนิดในทุกๆ เว็บบราว์เซอร์ ในการเปรียบเทียบ คอมโพแนนต์ของ Vue ไม่ต้องการ polyfill และงานอย่างสม่ำเสมอใดๆ ในการรองรับของเว็บบราว์เซอร์ (IE9 ขึ้นไป) เมื่อจำเป็น คอมโพแนนต์ของ Vue สามารถซ่อนข้างในส่วนประกอบกำหนดเองโดยกำเนิด

2. คอมโพแนนต์ของ Vue จะให้ความสามารถที่สำคัญที่ไม่ได้อยู่ในส่วนประกอบที่กำหนดเอง โดยส่วนใหญ่การส่งผ่านข้อมูลข้ามคอมโพแนนต์ เหตุการณ์ที่กำหนดเอง และสร้างเครื่องมือที่ใช้ในการรวบรวมระบบ

## พร้อมสำหรับข้อมูลเพิ่มเติม?

เราอธิบายคุณสมบัติเบื้องต้นมากสำหรับส่วนหลักของ Vue.js - ส่วนที่เหลือของคำแนะนำนี้จะครอบคลุมสิ่งที่อธิบายไปแล้วและคุณสมบัติอื่นในขั้นสูงขึ้นด้วยรายละเอียดเพิ่มเติม ดังนั้นคุณอาจจะอ่านทั้งหมดเพื่อความเข้าใจอย่างลึกซึ้ง

<div id="video-modal" class="modal"><div class="video-space" style="padding: 56.25% 0 0 0; position: relative;"><iframe src="https://player.vimeo.com/video/247494684" style="height: 100%; left: 0; position: absolute; top: 0; width: 100%; margin: 0" frameborder="0" webkitallowfullscreen mozallowfullscreen allowfullscreen></iframe></div><script src="https://player.vimeo.com/api/player.js"></script></div>
