# vuejs.org / th.vuejs.org ภาษาไทย

เว็บไซต์นี้สร้างด้วย [hexo](http://hexo.io/) เนื้อหาทั้งหมดเขียนด้วยรูปแบบ markdown format อยู่ในโฟลเดอร์ `src` ยินดีสำหรับการร่วมการแปลเว็บวิวเจเอสให้เป็นภาษาไทยด้วยการ pull request การแปลมาได้เลยครับ

## การพัฒนา

``` bash
$ npm install
$ npm start # dev server at http://localhost:4000
```

## การนำไปใช้

เว็บไซต์สร้างการนำไปใช้ (deploy) ไว้แบบอัตโนมัตเมื่อมีการ commit ไปที่ `master` ด้วย [Netlify](https://www.netlify.com/)

## การแปล

สำหรับโครงการการแปลเป็นภาษาต่างๆ ของเว็บไซต์จะถูกเก็บไว้โดยการแยก repository ที่ถูก fork จากเว็บไซต์ต้นฉบับ ตามภาษาต่างๆ

### ภาษาไทย

การแปลเป็นภาษาไทยจะถูกเก็บไว้ในกลุ่ม Vuejs-TH.

* Repo การแปล - [/vuejs-th/th.vuejs.org](https://github.com/vuejs-th/th.vuejs.org)

## วิธีการร่วมแปล

1. สามารถ fork vuejs-th/th.vuejs.org ไปยัง repos ของท่าน
2. อัพเดต **สถานะ** ว่าคุณกำลังแปลหน้าไหนอยู่ใน README.md เพื่อที่จะไม่ทำงานซ้อนกัน
3. หลังจากแปลเสร็จแล้ว อัพเดตสถานะและใส่ emoji :ballot_box_with_check: ในช่อง **เสร็จ?** ใน README.md  เพื่อบอกว่าเสร็จแล้วน่ะ
4. Pull request มาที่ vuejs-th/th.vuejs.org เพื่อ merge เข้ากับโปรเจคหลัก

> _มาช่วยกันแปลให้เสร็จน่ะครับ_

### **TODO:** ราการที่ต้องแปล

หน้า | สถานะ |  เสร็จ? |
----|:-------:|:--------:|
themes/vue/layout/partials/ecosystem_dropdown.ejs | เสร็จ | :ballot_box_with_check: |
themes/vue/layout/partials/language_dropdown.ejs | เสร็จ | :ballot_box_with_check: |
themes/vue/layout/partials/learn_dropdown.ejs | เสร็จ | :ballot_box_with_check: |
themes/vue/layout/partials/main_menu.ejs | เสร็จ | :ballot_box_with_check: |
themes/vue/layout/partials/sponsors_sidebar.ejs | เสร็จ | :ballot_box_with_check: |
themes/vue/layout/partials/sponsors.ejs |  เสร็จ | :ballot_box_with_check: |
themes/vue/layout/partials/support_vue_dropdown.ejs | เสร็จ | :ballot_box_with_check: |
v2/api/index.html | กำลังแปล | 
v2/guide/class-and-style.html
v2/guide/comparison.html
v2/guide/components.html
v2/guide/computed.html
v2/guide/conditional.html
v2/guide/custom-directive.html
v2/guide/deployment.html
v2/guide/events.html
v2/guide/forms.html
v2/guide/index.html | เสร็จ | :ballot_box_with_check: | 
v2/guide/installation.html | เสร็จ | :ballot_box_with_check: |
v2/guide/instance.html
v2/guide/join.html
v2/guide/list.html
v2/guide/migration-vue-router.html
v2/guide/migration-vuex.html
v2/guide/migration.html
v2/guide/mixins.html
v2/guide/plugins.html
v2/guide/reactivity.html
v2/guide/render-function.html
v2/guide/routing.html
v2/guide/single-file-components.html
v2/guide/ssr.html
v2/guide/state-management.html
v2/guide/syntax.html
v2/guide/transitioning-state.html
v2/guide/transitions.html
v2/guide/unit-testing.html
v2/examples/commits.html | เสร็จ | :ballot_box_with_check: |
v2/examples/elastic-header.html | เสร็จ | :ballot_box_with_check: |
v2/examples/firebase.html | เสร็จ | :ballot_box_with_check: |
v2/examples/grid-component.html | เสร็จ | :ballot_box_with_check: |
v2/examples/hackernews.html | เสร็จ | :ballot_box_with_check: |
v2/examples/index.html | เสร็จ | :ballot_box_with_check: |
v2/examples/modal.html | เสร็จ | :ballot_box_with_check: |
v2/examples/select2.html | เสร็จ | :ballot_box_with_check: |
v2/examples/svg.html | เสร็จ | :ballot_box_with_check: |
v2/examples/todomvc.html | เสร็จ | :ballot_box_with_check: |
v2/examples/tree-view.html | เสร็จ | :ballot_box_with_check: |
