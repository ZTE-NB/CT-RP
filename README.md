# Executive OLT Repeat Downtime & Root Cause Intelligence Dashboard

ระบบวิเคราะห์และแสดงผลข้อมูลการเกิดปัญหาซ้ำซาก (**Repeat Outage**) ของโครงข่ายชุมสาย **OLT** ย้อนหลัง 2 เดือน (16 ส.ค. 2026 – 16 ต.ค. 2026) เพื่อช่วยให้ผู้บริหารและทีมวิศวกรรมโครงข่ายมองเห็นว่า OLT ตัวไหนมีปัญหาเรื้อรัง สาเหตุที่แท้จริงคืออะไร และควร Focus แก้ไขที่จุดใด

---

## 🚀 ฟีเจอร์หลักของ Dashboard

- **KPI Ribbon สรุปภาพรวม:**
  - จำนวนเหตุการณ์ล่มทั้งหมด: **11,879 ครั้ง**
  - สัดส่วนปัญหาเกิดซ้ำซาก (**Repeat Rate**): **79.4%**
  - เวลาระบบหยุดทำงานสะสม (**Total Downtime**): **39,919 ชั่วโมง** (ปัญหาซ้ำคิดเป็น 75.9%)
  - สัดส่วน OLT ที่พบปัญหา Bug (**Software Bug OLT Rate**): **102 ชุมสาย (2.09%)** จาก 4,872 ชุมสาย
- **Executive Strategic Brief (4 เสาหลักที่ต้อง Focus):**
  - **P1 ไฟดับ (Power Outage - 63.7%):** เปลี่ยนแบตเตอรี่สำรอง LiFePO4 ให้ Top 50 OLT ไฟดับซ้ำ
  - **P2 สายไฟเบอร์ขาด (Fiber Cut - 20.1%):** ตัดแต่งกิ่งไม้เชิงรุก, ใส่เกราะกันสัตว์กัด, ทำ Dual Uplink
  - **P3 Bug Software OLT (0.9%):** แจ้ง Vendor Escalation (DASAN 52.3%, RAISECOM 13.1%) ออก Firmware Patch
  - **P4 การฟื้นตัวอัตโนมัติ (Auto-Recovered - 11.5%):** ตรวจเช็กระบบระบายความร้อน, ฝุ่นตู้ OLT, และ SFP
- **Interactive Visualizations (Chart.js):**
  - Donut Chart สัดส่วนตาม Category
  - Regional Outage Bar Chart (อีสานและเหนือ 67%)
  - Software Bug Breakdown by OLT Vendor Donut Chart
  - Top 15 Chronic OLTs Bar Chart
  - Weekly Trend Line Chart
- **Data Explorer & Filter Table:**
  - ค้นหา OLT ตามรหัส (CINAME), จังหวัด, อำเภอ, ยี่ห้อ
  - กรองระดับความรุนแรง (&ge;10 ครั้ง, &ge;5 ครั้ง, &ge;2 ครั้ง)
  - แท็บกรองแยกเฉพาะหมวดหมู่ (ไฟดับ Top 50, สายขาด Top 50, Bug Software, Auto-Recover)
  - ป๊อปอัป Modal เจาะลึกประวัติตั๋วรายครั้งของ OLT แต่ละตัว
  - ปุ่มส่งออกเป็นไฟล์ **CSV** และปุ่มพิมพ์รายงานสำหรับผู้บริหาร

---

## 📁 โครงสร้างไฟล์ใน Repository

| ไฟล์ | รายละเอียด |
| :--- | :--- |
| `index.html` | ตัว Dashboard ฉบับ Standalone พร้อมใช้งานทันที มีข้อมูลและกราฟทั้งหมดฝังในตัวไฟล์ รองรับ **GitHub Pages** ได้ทันทีโดยไม่ต้องพึ่งพา Backend |
| `README.md` | เอกสารอธิบายภาพรวมโครงการ, ดัชนี KPI สำคัญสำหรับผู้บริหาร, และคำแนะนำการใช้งาน |


---

## 🌐 การนำขึ้น GitHub & เปิดใช้งาน GitHub Pages

### 1. Initialize Git และ Push ขึ้น Repository

```bash
cd /home/iphuch-pi/git
git init
git add .
git commit -m "feat: Initial commit for Executive OLT Repeat Downtime Dashboard"
git branch -M main
git remote add origin <YOUR_GITHUB_REPOSITORY_URL>
git push -u origin main
```

### 2. เปิดใช้งาน GitHub Pages เพื่อดู Dashboard ออนไลน์

1. ไปที่หน้า Repository ของคุณบน GitHub
2. ไปที่ **Settings** > **Pages**
3. ที่ส่วน **Build and deployment** ให้เลือก **Branch: `main`** และโฟลเดอร์ **`/ (root)`** แล้วกด **Save**
4. ระบบจะเปิดให้เข้าใช้งาน Dashboard ออนไลน์ผ่าน URL:  
   `https://<your-username>.github.io/<repository-name>/`
