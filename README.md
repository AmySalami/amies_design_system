# Amie's Design System

[![Open Storybook](https://img.shields.io/badge/Open-Storybook-ffc400?style=for-the-badge&labelColor=1e3258)](https://amysalami.github.io/amies_design_system/amies-design-system.html)

เปิด live preview: https://amysalami.github.io/amies_design_system/amies-design-system.html

ระบบดีไซน์กลาง (design tokens และ components ที่ใช้ซ้ำ) สำหรับทุกโปรเจกต์
นี่คือ single source of truth แก้ token ที่นี่ที่เดียว

## โครงสร้าง

```
.
├── amies-design-system.css     # tokens (สี ฟอนต์ spacing radius elevation)
├── amies-design-system.html    # storybook / หน้า preview ของระบบ
└── README.md
```

repo นี้มีแค่ "ตัวระบบ" กับ "หน้า preview" เท่านั้น โปรเจกต์ที่ใช้งานจริง
(พอร์ต, product) เป็น consumer แยก repo ไม่อยู่ในนี้

## preview บนเครื่อง

```bash
python3 -m http.server 8000
```

เปิด `http://localhost:8000/amies-design-system.html`
(ต้องเสิร์ฟผ่าน http ไม่ใช่ดับเบิลคลิกเปิดไฟล์ตรง ๆ)

## แก้ token

แก้ค่าใน `amies-design-system.css` (เช่น `--accent`) แล้ว commit + push
หน้า preview จะอัปเดตทันที ส่วน consumer แต่ละตัวต้อง sync ตาม
(ดู process ใน README ของ repo นั้น)

## แนวคิดการแบ่งชั้น (layer)

ของที่ควรอยู่ใน repo นี้ vs อยู่กับโปรเจกต์เอง:

- **Foundations (อยู่ที่นี่):** tokens ทั้งหมด ใช้ร่วมกันได้ทุกโปรเจกต์
- **Shared components (อยู่ที่นี่ได้):** ปุ่ม badge card ที่ใช้ซ้ำจริงหลายโปรเจกต์
- **Component เฉพาะโปรเจกต์ (อยู่กับโปรเจกต์):** เช่น roadmap หรือ pull quote
  ของพอร์ต, data table หรือ form ของ product อย่ายัดเข้าระบบกลาง

> หลักคิด: ถ้ามันใช้ซ้ำจริงค่อยยกขึ้นมากลาง อย่ายกของที่ใช้ที่เดียว

## หลักการใช้สี

- **Primary `--accent` (#ffc400)** ใช้กับพื้นและไอคอนเท่านั้น ไม่ใช้กับตัวอักษร
- **Secondary `--secondary` (#1e3258)** ใช้กับหัวข้อ label และตัวอักษรบนพื้น primary

## โฮสต์ออนไลน์

push ขึ้น GitHub แล้วเปิด GitHub Pages หรือเชื่อม Netlify / Vercel
เพื่อให้หน้า storybook มีลิงก์เว็บให้ทีมเปิดดูได้
