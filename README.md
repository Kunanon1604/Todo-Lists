# 📋 Todo App — Google Sheets + GitHub Pages

Web App จัดการ Todo List โดยเก็บข้อมูลใน Google Sheets ผ่าน Google Apps Script

---

## 🗂 โครงสร้างไฟล์

```
todo-app/
├── index.html     ← Web App หลัก (ไฟล์เดียว)
├── Code.gs        ← Google Apps Script (Backend)
└── README.md      ← คู่มือนี้
```

---

## ✅ ฟีเจอร์

- เพิ่ม / ลบ Task
- Mark เสร็จ / ยังไม่เสร็จ
- Due Date + Priority (High / Medium / Low)
- ค้นหา + Filter (ทั้งหมด / รอทำ / เสร็จแล้ว)
- สถิติ tasks ที่ด้านบน
- ซิงค์ข้อมูลกับ Google Sheets
- Dark Mode อัตโนมัติ
- Responsive ทุกขนาดหน้าจอ

---

## 🔧 ขั้นตอนที่ 1 — ตั้งค่า Google Apps Script

### 1.1 สร้าง Google Spreadsheet

1. เปิด [Google Sheets](https://sheets.google.com)
2. กด **+ Blank** สร้าง Spreadsheet ใหม่
3. ตั้งชื่อตามชอบ เช่น "Todo App Data"

### 1.2 เปิด Apps Script

1. ใน Google Sheets คลิกเมนู **Extensions → Apps Script**
2. ลบโค้ดเดิมออกทั้งหมด
3. คัดลอกโค้ดจากไฟล์ `Code.gs` ในโปรเจกต์นี้วางแทน
4. กด **💾 Save** (Ctrl+S)

### 1.3 Deploy เป็น Web App

1. คลิก **Deploy → New deployment**
2. คลิกไอคอน ⚙️ ข้าง **Select type** แล้วเลือก **Web app**
3. ตั้งค่าดังนี้:
   - **Description**: Todo App API
   - **Execute as**: Me
   - **Who has access**: **Anyone** ← สำคัญมาก!
4. กด **Deploy**
5. คลิก **Authorize access** และอนุญาต
6. **คัดลอก URL** ที่ได้ — จะหน้าตาแบบนี้:

```
https://script.google.com/macros/s/AKfycbxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxx/exec
```

---

## 🌐 ขั้นตอนที่ 2 — เชื่อม Web App กับ Google Sheets

1. เปิดไฟล์ `index.html` ในเบราว์เซอร์
2. จะเห็น banner เตือนสีเหลืองด้านบน
3. คลิก **"คลิกตั้งค่าตอนนี้"**
4. วาง URL ของ Apps Script ที่ได้จาก Step 1.3
5. กด **บันทึก**
6. แอปจะซิงค์ข้อมูลอัตโนมัติ ✓

---

## 🚀 ขั้นตอนที่ 3 — Deploy ขึ้น GitHub Pages

### 3.1 สร้าง Repository

```bash
# เข้าไปในโฟลเดอร์โปรเจกต์
cd todo-app

# Init Git
git init
git add index.html README.md
git commit -m "Initial commit: Todo App"
```

### 3.2 สร้าง Repo บน GitHub

1. เปิด [github.com/new](https://github.com/new)
2. ตั้งชื่อ Repository เช่น `todo-app`
3. เลือก **Public**
4. **อย่า** check "Add README" (เรามีของเราแล้ว)
5. กด **Create repository**

### 3.3 Push โค้ด

```bash
git remote add origin https://github.com/YOUR_USERNAME/todo-app.git
git branch -M main
git push -u origin main
```

> แทน `YOUR_USERNAME` ด้วย GitHub username ของคุณ

### 3.4 เปิด GitHub Pages

1. ไปที่ Repository บน GitHub
2. คลิก **Settings** → **Pages**
3. ตรง **Source** เลือก **Deploy from a branch**
4. เลือก Branch: **main** / folder: **/ (root)**
5. กด **Save**
6. รอ 1-2 นาที แล้ว URL จะปรากฏ:

```
https://YOUR_USERNAME.github.io/todo-app/
```

---

## 🔄 การอัปเดตในอนาคต

แก้ไข `index.html` แล้วรันคำสั่ง:

```bash
git add index.html
git commit -m "Update: [ระบุสิ่งที่เปลี่ยน]"
git push
```

GitHub Pages จะ deploy อัตโนมัติภายใน 1-2 นาที

---

## ❓ แก้ปัญหา

| ปัญหา | วิธีแก้ |
|-------|---------|
| ซิงค์ไม่ได้ | ตรวจสอบว่า Apps Script ตั้ง "Who has access: Anyone" |
| URL ขึ้น error | Re-deploy Apps Script แล้วคัดลอก URL ใหม่ |
| ข้อมูลไม่ขึ้นใน Sheets | เช็ค Sheet ชื่อ "Tasks" ใน Spreadsheet |
| GitHub Pages ไม่แสดง | ตรวจสอบ Settings → Pages ว่า source ถูกต้อง |

---

## 📊 โครงสร้างข้อมูลใน Google Sheets

| ID | Title | Done | Priority | Due Date | Created At |
|----|-------|------|----------|----------|------------|
| 1718123456789 | ทำรายงาน | FALSE | high | 2025-06-20 | 2025-06-18T... |
| 1718123456790 | ซื้อของ | TRUE | low | | 2025-06-18T... |

---

สร้างด้วย ❤️ — HTML/CSS/JS + Google Apps Script
