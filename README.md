# 🏨 Mansion POS (ระบบจัดการแมนชั่นรายวัน)

ระบบ Web Application สำหรับบริหารจัดการแมนชั่นและหอพักรายวัน (Daily Rental Mansion Management System) พัฒนาด้วย Node.js และ MySQL โดยเน้นความใช้งานง่าย ทันสมัย และรองรับการทำงานผ่าน Mobile Web

## ✨ ฟีเจอร์หลัก (Key Features)

### 1. 📊 แดชบอร์ด (Dashboard)
- ดูภาพรวมสถานะห้องพักทั้งหมดได้ในหน้าเดียว
- แสดงสถิติประจำวัน: จำนวนเช็คอิน, เช็คเอาท์, รายได้วันนี้, และผู้เข้าพักที่ยังพักอยู่
- กราฟิกแสดงสถานะห้อง: 🟢 ว่าง, 🔴 มีผู้เข้าพัก, 🟡 กำลังทำความสะอาด

### 2. 🚪 จัดการห้องพัก (Room Management)
- ดูสถานะห้องพักรายห้อง
- เปลี่ยนสถานะห้องพักได้ทันที (เช่น แจ้งทำความสะอาดเมื่อแขกออก)
- รองรับห้องพักหลายประเภท (เตียงเดี่ยว/เตียงคู่)

### 3. 👤 จัดการผู้เข้าพัก (Guest Management)
- บันทึกข้อมูลผู้เข้าพัก: ชื่อ-นามสกุล, เลขบัตรประชาชน, เบอร์โทร, ที่อยู่
- 🔍 **ค้นหาข้อมูลลูกค้าเก่า** ได้จากเลขบัตรประชาชน (ระบบจดจำลูกค้าเก่า)
- ดูประวัติผู้เข้าพักย้อนหลัง

### 4. 📥 ระบบเช็คอิน (Check-in)
- Flow การทำงานแบบ Step-by-step ใช้งานง่าย
- คำนวณค่าห้องและค่ามัดจำกุญแจให้อัตโนมัติ
- รองรับการจ่ายเงินหลายรูปแบบ (เงินสด, โอนเงิน, บัตรเครดิต)

### 5. 📤 ระบบเช็คเอาท์ (Check-out)
- ตรวจสอบวันเวลาเช็คเอาท์อัตโนมัติ
- **ระบบคำนวณค่าปรับอัตโนมัติ** (Late Fee) หากเกินเวลาที่กำหนด (หลัง 12:00 น.)
- จัดการการคืนเงินมัดจำ (Deposit Return)
- เปลี่ยนสถานะห้องเป็น "ทำความสะอาด" อัตโนมัติหลังเช็คเอาท์

### 6. 💰 การเงินและรายงาน (Payments & Reports)
- บันทึกประวัติการรับเงินทุกยอด (ค่าห้อง, ค่าปรับ, เงินมัดจำ)
- 📈 **รายงานรายเดือน**: สรุปยอดรายรับ, จำนวนลูกค้า, อัตราการเข้าพัก แยกตามวันและประเภทห้อง

### 7. 🔐 ระบบกำหนดสิทธิ์การใช้งาน (Role-Based Access Control)
- **ผู้จัดการ / เจ้าของ (Owner):** สามารถเข้าถึงทุกเมนู บันทึกรายได้ ดูรายงาน และจัดการภาพรวมระบบ
- **แม่บ้าน (Housekeeper):** หน้าจอถูกปรับให้เห็นเฉพาะเมนู "จัดการห้องพัก" เพื่อให้สามารถดูห้องที่ต้องทำความสะอาด และเปลี่ยนสถานะห้องเมื่อทำเสร็จ โดยไม่ต้องเผยแพร่ข้อมูลการเงิน

---

## 🛠️ Tech Stack

### 💻 Frontend (ส่วนหน้าบ้าน)
- **HTML5 & CSS3**: ใช้โครงสร้างและมาตรฐานเว็บล่าสุด เน้นการเขียน CSS เอง (Vanilla CSS) เพื่อให้ได้ Design ที่เป็นเอกลักษณ์ สวยงาม และโหลดไว ไม่หนัก Framework
- **JavaScript (Vanilla)**: เขียน Logic การทำงานด้วย JavaScript เพียวๆ ไม่ผ่าน Framework (เช่น React/Vue) ทำให้โค้ดคลีน แก้ไขง่าย และไม่ต้องมีการ Build file ที่ซับซ้อน เหมาะสำหรับระบบที่ต้องการความเสถียรและดูแลรักษาง่าย
- **Modern UI Design**: ออกแบบโดยเน้น User Experience (UX) ที่ดี มีความทันสมัย สะอาดตา และรองรับการใช้งานผ่านมือถือ (Responsive)

### 🔙 Backend (ส่วนหลังบ้าน)
- **Node.js**: เลือกใช้เพราะทำงานได้รวดเร็ว (Non-blocking I/O) รองรับการเรียกใช้ API จำนวนมากได้พร้อมกัน
- **Express.js**: Framework ยอดนิยมสำหรับทำ RESTful API ช่วยจัดการ Routing และ Middleware ให้เป็นระเบียบ

### 🗄️ Database (ฐานข้อมูล)
- **MySQL**: ฐานข้อมูลแบบ Relational Database (RDBMS) เหมาะสำหรับการเก็บข้อมูลที่มีความสัมพันธ์กันซับซ้อน เช่น ลูกค้า -> การจอง -> การชำระเงิน ทำให้ข้อมูลมีความถูกต้องแม่นยำ (Data Integrity) สูง

### 🧪 Testing (การทดสอบ)
- **Jest & Supertest**: ใช้เขียน Automated Test เพื่อตรวจสอบความถูกต้องของ API ทุกเส้นก่อนนำไปใช้งานจริง ป้องกันบั๊กที่อาจเกิดขึ้นเมื่อมีการแก้ไขโค้ด

---

## ⚙️ การติดตั้งและเริ่มต้นใช้งาน (Installation)

### 1. สิ่งที่ต้องมี (Prerequisites)
- [Node.js](https://nodejs.org/) (v18 ขึ้นไป)
- [MySQL Server](https://dev.mysql.com/downloads/installer/)

### 2. ติดตั้งโปรเจค
```bash
# Clone โปรเจค (ถ้ามี git) หรือดาวน์โหลดไฟล์
git clone <repository_url>
cd mansion-pos

# ติดตั้ง dependencies
npm install
```

### 3. ตั้งค่าฐานข้อมูล (Database Setup)
1. ตรวจสอบว่า MySQL Server ทำงานอยู่
2. สร้าง Database และ Table โดยรันคำสั่ง:
```bash
# วิธีที่ 1: รันผ่าน npm script (ถ้ามี)
npm run init-db

# วิธีที่ 2: Import ไฟล์ SQL โดยตรง
mysql -u root -p < init-db.sql
```
*หมายเหตุ: ไฟล์ `init-db.sql` จะทำการสร้าง database ชื่อ `mansion_pos` และตารางที่จำเป็นทั้งหมด พร้อมข้อมูลห้องพักตัวอย่าง*

### 4. ตั้งค่า Environment Variables (.env)
สร้างไฟล์ `.env` ใน root folder และกำหนดค่าดังนี้:
```env
PORT=3000
DATABASE_URL=mysql://root:password@localhost:3306/mansion_pos
# หรือแยกเป็นค่าๆ
MYSQL_HOST=localhost
MYSQL_PORT=3306
MYSQL_USER=root
MYSQL_PASSWORD=your_password_here
MYSQL_DATABASE=mansion_pos
```

### 5. รันโปรแกรม (Start Server)
```bash
# โหมด Development
npm run dev

# หรือ
node server.js
```
เปิด Browser และเข้าใช้งานที่: `http://localhost:3000`

---

## 🚚 การย้ายไปติดตั้งบนเครื่องอื่น (Migration Guide)

หากต้องการนำโปรเจคนี้ไปรันบนคอมพิวเตอร์เครื่องอื่น ให้ทำตามขั้นตอนดังนี้:

1. **Copy Files**: ก๊อปปี้โฟลเดอร์โปรเจคทั้งหมดไปไว้ที่เครื่องใหม่
2. **Install Node.js & MySQL**: ตรวจสอบว่าเครื่องใหม่ติดตั้ง [Node.js](https://nodejs.org/) และ [MySQL](https://dev.mysql.com/downloads/installer/) เรียบร้อยแล้ว
3. **Database Setup**:
    - สร้าง Database และ Table ใหม่ โดยใช้ไฟล์ `init-db.sql`
    - สามารถใช้คำสั่ง `mysql -u root -p < init-db.sql` หรือใช้โปรแกรมอย่าง MySQL Workbench / phpMyAdmin import เข้าไป
4. **Environment Config**:
    - สร้างไฟล์ `.env` บนเครื่องใหม่ (หรือก๊อปปี้ไฟล์ `.env` เดิมไป)
    - **สำคัญ:** แก้ไขค่า `MYSQL_PASSWORD` ในไฟล์ `.env` ให้ตรงกับรหัสผ่านของ MySQL ในเครื่องใหม่
5. **Start Server**:
    - เปิด Terminal ในโฟลเดอร์โปรเจค
    - รันคำสั่ง `npm install` (หากไม่ได้ก๊อปปี้โฟลเดอร์ `node_modules` มาด้วย หรือเพื่อความชัวร์)
    - รันคำสั่ง `npm run dev` เพื่อเริ่มใช้งาน

### 📌 สำหรับเครื่องที่ใช้ XAMPP
หากเครื่องปลายทางใช้ **XAMPP / WAMP / MAMP**:
1. เปิด **XAMPP Control Panel** และกด Start **Apache** และ **MySQL**
2. เข้าไปที่ `http://localhost/phpmyadmin`
3. สร้าง Database ใหม่ชื่อ `mansion_pos` (Encoding: `utf8mb4_general_ci`)
4. **วิธีการ Import ไฟล์ SQL**:
    - คลิกที่ชื่อ Database `mansion_pos` ที่แถบซ้ายมือ
    - คลิกที่แท็บ **Import** (เมนูด้านบน)
    - ที่หัวข้อ **File to import**: กดปุ่ม **Choose File** (หรือ Browse)
    - เลือกไฟล์ `init-db.sql` ที่อยู่ในโฟลเดอร์โปรเจคนี้
    - เลื่อนลงมาด้านล่างสุด แล้วกดปุ่ม **Import** หรือ **Go**
5. แก้ไขไฟล์ `.env`:
    - `MYSQL_PORT`: ปกติ XAMPP ใช้ `3306` (เช็คใน Control Panel)
    - `MYSQL_USER`: `root`
    - `MYSQL_PASSWORD`: ปกติจะเป็นค่าว่าง (ลบข้อความหลังเครื่องหมาย `=` ออก) หรือตามที่ตั้งไว้

---

## 📂 โครงสร้างโปรเจค (Project Structure)

```
mansion-pos/
├── public/              # ไฟล์ Frontend (HTML, CSS, JS)
│   ├── index.html       # หน้าเว็บหลัก (Single Page Application)
│   ├── style.css        # Stylesheet
│   └── app.js           # Frontend Logic & API Integration
├── scripts/             # Scripts สำหรับตั้งค่าระบบ
│   └── init-db.js       # Script สร้างฐานข้อมูล
├── tests/               # Unit & Integration Tests
├── init-db.sql          # SQL Script สำหรับสร้าง Schema
├── server.js            # ไฟล์หลัก Backend Server (Express)
├── package.json         # รายชื่อ Dependencies และ Scripts
└── .gitignore           # Git ignore config
```

---

## 🔌 API Endpoints (เบื้องต้น)

| Create | Endpoint | Description |
|--------|----------|-------------|
| GET | `/api/guests` | ดึงข้อมูลผู้เข้าพักทั้งหมด |
| POST | `/api/guests` | เพิ่มผู้เข้าพักใหม่ |
| GET | `/api/rooms` | ดึงข้อมูลห้องพักและสถานะ |
| POST | `/api/checkin` | ทำรายการเช็คอิน |
| POST | `/api/checkout/:id` | ทำรายการเช็คเอาท์ |
| GET | `/api/reports/monthly` | ดูรายงานรายเดือน |

---

## 🔐 Security Information
- ระบบมีการป้องกัน SQL Injection เบื้องต้นด้วยการใช้ Parameterized Queries
- ข้อมูลส่วนตัวลูกค้าถูกเก็บใน Database ที่แยกเป็นสัดส่วน

---

## 🤝 Contributing
1. Fork โปรเจค
2. สร้าง Feature Branch (`git checkout -b feature/NewFeature`)
3. Commit Changes (`git commit -m 'Add some NewFeature'`)
4. Push ไปยัง Branch (`git push origin feature/NewFeature`)
5. เปิด Pull Request
