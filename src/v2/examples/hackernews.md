---
title: การโคลน HackerNews 
type: examples
order: 12
---

> นี่เป็นโคลนโปรเจคของ HackerNews ที่สร้างขึ้นจาก API Firebase อย่างเป็นทางการของ HN , Vue 2.0 + Vue Router + Vuex, โดยจะการแสดงผลในฝั่งเซิร์ฟเวอร์

{% raw %}
<div style="max-width: 600px;">
  <a href="https://github.com/vuejs/vue-hackernews-2.0" target="_blank">
    <img style="width: 100%;" src="../../images/hn.png">
  </a>
</div>
{% endraw %}

> [ตัวอย่าง](https://vue-hn.now.sh/)
> หมายเหตุ: การสาธิตอาจต้องรอบางเวลา ถ้าไม่มีใครมีเข้ามาเป็นระยะ
>
> [[ข้อมูล](https://github.com/vuejs/vue-hackernews-2.0)]

## คุณสมบัติ

- ฝั่งเซิร์ฟเวอร์แสดงผล
  - Vue + Vue Router + Vuex ที่ทำงานร่วมกัน
  - ฝั่งเซิร์ฟเวอร์ข้อมูลดึงข้อมูลล่วงหน้า
  - ด้านลูกค้าสถานะ ดอม ไฮเดรชั่น
- ส่วนคอมโพเนนต์แบบไฟล์เดียว
  - จะสามารถ Hot-reload ได้ ในการพัฒนา
  - แยกส่วนของ CSS ในการสร้าง
- อัพเดทแบบเรียลไทม์ แบบ FLIP อนิเมชั่น

## ภาพโดยรวมของสถาปัตยกรรม

<img width="973" alt="Hackernew clone architecture overview" src="../../images/hn-architecture.png">
