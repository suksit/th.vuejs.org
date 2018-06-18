---
หัวข้อ: Routing
ประเภท: การแนะนำ
ลำดับที่: 501
---

## Official Router

สำหรับแอ๊พพลิเคชั่นหน้าเดียวส่วนมาก จะแนะนำให้ใช้ [ไลบรารี่ vue-router](https://github.com/vuejs/vue-router) ที่ได้รับการสนับสนุนอย่างเป็นทางการ สำหรับรายละเอียดอื่นๆ ดูได้ที่ [เอกสารคู่มือ vue-router's](https://router.vuejs.org/).

## ตัวอย่างการจัดการ Routing อย่างง่าย

ถ้าคุณต้องการแค่การจัดการ Routing อย่างง่ายๆ และไม่ต้องการไปยุ่งเกี่ยวกับ ไลบรารี่ vue-router คุณสามารถทำการแสดงคอมโพเน้นของหน้าเว็บแต่ละระดับ ได้แบบนี้

``` js
const NotFound = { template: '<p>Page not found</p>' }
const Home = { template: '<p>home page</p>' }
const About = { template: '<p>about page</p>' }

const routes = {
  '/': Home,
  '/about': About
}

new Vue({
  el: '#app',
  data: {
    currentRoute: window.location.pathname
  },
  computed: {
    ViewComponent () {
      return routes[this.currentRoute] || NotFound
    }
  },
  render (h) { return h(this.ViewComponent) }
})
```

ทำงานร่วมกับตัวจัดการ HTML5(HTML5 History API) คุณสามารถสร้างมันได้อย่างง่ายๆ แต่สามารถทำงานได้เต็มประสิทธิภาพ โดยการทำงานฝั่ง Client คุณสามารถดูได้ที่ตัวอย่างนี้ [นี่คือตัวอย่าง Routing](https://github.com/chrisvfritz/vue-2.0-simple-routing-example).

## การทำงานร่วมกันกับส่วนเสริม 3rd-Party Routers

ถ้าหากมี 3rd-party router ที่คุณชอบใช้, อย่างเช่น [Page.js](https://github.com/visionmedia/page.js) หรือ [Director](https://github.com/flatiron/director) ที่ทำงานร่วมกันกับ [similarly easy](https://github.com/chrisvfritz/vue-2.0-simple-routing-example/compare/master...pagejs) นี่คือ [complete example](https://github.com/chrisvfritz/vue-2.0-simple-routing-example/tree/pagejs) ที่มีการใช้งาน Page.js.
