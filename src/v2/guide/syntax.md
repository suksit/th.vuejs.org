---
title:  ไวยกรณ์เทมเพลต
type: guide
order: 4
---

Vue.js ใช้ไวยกรณ์เทมเพลตโดยใช้พื้นฐาน HTML ที่ทำให้คุณประกาศผูกการแสดงผล DOM กับอินสแตนส์ Vue ที่อยู่ในเบื้องหลัง เทมเพลต Vue.js ทั้งหมดใช้ได้กับ HTML ที่สามารถวิเคราะห์คำด้วยสเปกที่สอดคล้องของเว็บเบราเซอร์และการวิเคราะห์คำของ HTML

ในเบื้องหลัง Vue จะคอมไฟล์เทมเพลตไปเป็นฟังก์ชันแสดงผล DOM เสมือนจริง รวบรวมกับระบบตอบสอนงทันที Vue สามารถชาญฉลาดในการหาคอมโพแนนส์ที่น้อยที่สุดเพื่อแสดงผลใหม่และใช้งานการจัดการ DOM จำนวนน้อยที่สุดเมื่อสถานะของแอพพลิเคชันเปลี่ยนแปลง

ถ้าคุณคุ้นเคยกับแนวคิดของ DOM เสมือนจริงและต้องการพลังดิบของ JavaScript, คุณสามารถดูเพิ่มเติมได้ที่ [เขียนฟังก์ชันแสดงผลโดยตรง](render-function.html) แทนที่เทมเพลต ด้วยตัวเลือกสนับสนุน JSX

## การแก้ไข

### ข้อความ

รูปแบบพื้นฐานที่สุดของผูกข้อมูลคือการแก้ไขข้อความใช้ไวยกรณ์ "หนวด" (วงเล็บปีกาคู่)

``` html
<span>Message: {{ msg }}</span>
```

แท็กหนวดจะถูกแทนที่ด้วยค่าของคุณสมบัติ `msg` บนวัตถุข้อมูลที่เกี่ยวข้อง นอกจากนี้ยังมีการอัปเดตเมื่อมีการเปลี่ยนแปลงคุณสมบัติ `msg` ของวัตถุ

นอกจากนี้คุณสามารถดำเนินการแก้ไขข้อมูลเพียงครั้งเดียวที่ไม่ได้อัปเดตเกี่ยวกับการเปลี่ยนแปลงข้อมูลโดยใช้คำสั่ง [v-once](../api/#v-once) แต่โปรดจำไว้ว่านี่จะส่งผลต่อการผูกอื่นในโหลดเดียวกัน:

``` html
<span v-once>This will never change: {{ msg }}</span>
```

### HTML ดิบ

หนวดคู่ตีความข้อมูลเป็นข้อความล้วนที่ไม่ใช้ HTML เพื่อที่จะสร้าง HTML จริง คุณจะต้องใช้คำสั่ง `v-html`

``` html
<p>Using mustaches: {{ rawHtml }}</p>
<p>Using v-html directive: <span v-html="rawHtml"></span></p>
```

{% raw %}
<div id="example1" class="demo">
  <p>Using mustaches: {{ rawHtml }}</p>
  <p>Using v-html directive: <span v-html="rawHtml"></span></p>
</div>
<script>
new Vue({
  el: '#example1',
  data: function () {
  	return {
  	  rawHtml: '<span style="color: red">This should be red.</span>'
  	}
  }
})
</script>
{% endraw %}

เนื้อหาของ `span` จะถูกแทนที่ด้วยค่าของคุณสมบัติ `rawHtml` ซึ่งแปลว่า HTML ธรรมดา -  การผูกข้อมูลจะถูกละเว้น โปรดทราบว่าคุณไม่สามารถใช้ `v-html` ในการเขียนแม่แบบเทมเพลตบางส่วนได้ เพราะว่า Vue ไม่ใช้เครืองมือเทมเพลตแบบสติง แทนที่จะเป็นคอมโพแนนต์ที่เหมาะสำหรับการใช้ซ้ำและองค์ประกอบของ UI

<p class="tip">การแสดงผลโดยทันทีแบบพลวัตบนเว็บไซต์ของคุณอาจจะเป็นอันตรายได้เนื่องจากอาจทำให้เกิด [ช่องโหว่ XSS](https://en.wikipedia.org/wiki/Cross-site_scripting) ใช้เฉพาะการแก้ไข HTML บนเนื้อหาที่เชื่อถือได้และ **ไม่ควรใช้** เนื้อหาที่ผู้ใช้ระบุ</p>

### แอตทริบิวต์

ไม่สามารถใช้หนวดในแอตทริบิวต์ของ HTML ได้ ใช้คำสั่ง [v-bind](../api/#v-bind):

``` html
<div v-bind:id="dynamicId"></div>
```

ในกรณีของคุณลักษณะบูลีนที่ค่าของมันจะเป็น `true`, `v-bind` ทำงานแตกต่างกันเล็กน้อย ในตัวอย่างนี้:

``` html
<button v-bind:disabled="isButtonDisabled">Button</button>
```

ถ้า `isButtonDisabled`มีค่าเป็น `null`, `undefined` หรือ `false` ค่าแอตทริบิวต์ `disabled` จะไม่ถูกรวมไว้ในการแสดงผลส่วน `<button>`

### ใช้นิพจน์ JavaScript

จนถึงขณะนี้เราเพียงผูกคีย์ของคุณสมบัติอย่างง่ายดายในเทมเพลต แต่ Vue.js รองรับนิพจน์ JavaScript เต็มรูปแบบภายใจการผูกข้อมูลทั้งหมด:

``` html
{{ number + 1 }}

{{ ok ? 'YES' : 'NO' }}

{{ message.split('').reverse().join('') }}

<div v-bind:id="'list-' + id"></div>
```

นิพจน์เหลานี้จะประเมินเป็น JavaScript ในขอบเขตของข้อมูลของอินสแตนส์ Vue หนึ่งในข้อจำกัดคือการผูกแต่ละครั้งสามารถมีได้เพียง **นิพจย์เดี่ยว** ดังนั้นโค้ดด้านล่างนี้จะ **ไม่** ทำงาน:

``` html
<!-- this is a statement, not an expression: -->
{{ var a = 1 }}

<!-- flow control won't work either, use ternary expressions -->
{{ if (ok) { return message } }}
```
<p class="tip">นิพจน์เทมเพลตเป็นแซนบล็อกและมีเพียงเข้าถึง whitelist ของโกลบอล เช่น `Math` และ `Date` คุณไม่ควรพยายามเข้าถึงโกลบอลที่กำหนดโดยผู้ใช้ในนิพจน์เทมเพลต</p>

## ตำสั่ง

คำสั่ง (Directive) เป็นแอตทริบิวต์พิเศษด้วยคำนำหน้า `v-` ค่าของแอตทริบิวต์คำสั่งคาดว่าจะเป็น ****
Directives are special attributes with the `v-` prefix. Directive attribute values are expected to be **a single JavaScript expression** (with the exception for `v-for`, which will be discussed later). A directive's job is to reactively apply side effects to the DOM when the value of its expression changes. Let's review the example we saw in the introduction:

``` html
<p v-if="seen">Now you see me</p>
```

Here, the `v-if` directive would remove/insert the `<p>` element based on the truthiness of the value of the expression `seen`.

### Arguments

Some directives can take an "argument", denoted by a colon after the directive name. For example, the `v-bind` directive is used to reactively update an HTML attribute:

``` html
<a v-bind:href="url"> ... </a>
```

Here `href` is the argument, which tells the `v-bind` directive to bind the element's `href` attribute to the value of the expression `url`.

Another example is the `v-on` directive, which listens to DOM events:

``` html
<a v-on:click="doSomething"> ... </a>
```

Here the argument is the event name to listen to. We will talk about event handling in more detail too.

### Modifiers

Modifiers are special postfixes denoted by a dot, which indicate that a directive should be bound in some special way. For example, the `.prevent` modifier tells the `v-on` directive to call `event.preventDefault()` on the triggered event:

``` html
<form v-on:submit.prevent="onSubmit"> ... </form>
```

You'll see other examples of modifiers later, [for `v-on`](events.html#Event-Modifiers) and [for `v-model`](forms.html#Modifiers), when we explore those features.

## Shorthands

The `v-` prefix serves as a visual cue for identifying Vue-specific attributes in your templates. This is useful when you are using Vue.js to apply dynamic behavior to some existing markup, but can feel verbose for some frequently used directives. At the same time, the need for the `v-` prefix becomes less important when you are building a [SPA](https://en.wikipedia.org/wiki/Single-page_application) where Vue.js manages every template. Therefore, Vue.js provides special shorthands for two of the most often used directives, `v-bind` and `v-on`:

### `v-bind` Shorthand

``` html
<!-- full syntax -->
<a v-bind:href="url"> ... </a>

<!-- shorthand -->
<a :href="url"> ... </a>
```

### `v-on` Shorthand

``` html
<!-- full syntax -->
<a v-on:click="doSomething"> ... </a>

<!-- shorthand -->
<a @click="doSomething"> ... </a>
```

They may look a bit different from normal HTML, but `:` and `@` are valid chars for attribute names and all Vue.js supported browsers can parse it correctly. In addition, they do not appear in the final rendered markup. The shorthand syntax is totally optional, but you will likely appreciate it when you learn more about its usage later.
