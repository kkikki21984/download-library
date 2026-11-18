# Download Library

เว็บไซต์คลังรวมเอกสารสำหรับค้นหาและดาวน์โหลดไฟล์จากหน้าเว็บเดียว โดยออกแบบไว้สำหรับเอกสารทบทวนด้านวิศวกรรมความปลอดภัยและไฟล์ประกอบการเรียน

## เปิดใช้งานเว็บไซต์

- เว็บไซต์: https://kkikki21984.github.io/download-library/
- Repository: https://github.com/kkikki21984/download-library

เว็บไซต์เผยแพร่ด้วย GitHub Pages ผ่าน GitHub Actions เมื่อมีการ push ไปยัง branch `main` หรือสั่งรัน workflow ด้วยตนเอง

## ตั้งค่า GitHub Pages ครั้งแรก (จำเป็น)

Repository นี้ยังไม่ได้เปิด GitHub Pages และการเชื่อมต่ออัตโนมัติที่ใช้กับ ChatGPT ไม่มีสิทธิ์เปิด Pages ให้แทนเจ้าของ Repository ได้ จึงต้องตั้งค่าครั้งเดียวใน GitHub:

1. เปิด Repository แล้วเข้า **Settings**
2. เลือก **Pages** ในแถบเมนูด้านซ้าย
3. ในหัวข้อ **Build and deployment** ตั้ง **Source** เป็น **GitHub Actions**
4. บันทึกการตั้งค่า (ถ้ามีปุ่ม Save)
5. เปิดแท็บ **Actions** แล้วรอ workflow **Deploy static site to GitHub Pages** ทำงานจนขึ้น Success

หลังจากตั้งค่าครั้งแรกแล้ว การ push ไปยัง `main` จะสั่ง deploy เว็บไซต์โดยอัตโนมัติ

## โครงสร้างปัจจุบัน

- `index.html` — หน้าเว็บคลังไฟล์ พร้อมค้นหาและกรอง ZIP/PDF
- `.github/workflows/pages.yml` — workflow สำหรับเผยแพร่เว็บไซต์
- `README.md` — คู่มือโครงการ

## วิธีเพิ่มไฟล์ดาวน์โหลด

1. เพิ่มไฟล์จริงลงใน Repository เช่น โฟลเดอร์ `downloads/`
2. แก้ไข `index.html` เพื่อเพิ่มรายการเอกสารและลิงก์ไปยังไฟล์จริง เช่น `downloads/review-set-01.zip`
3. ตรวจสอบว่าชื่อไฟล์และนามสกุลตรงกับไฟล์ที่อัปโหลด
4. Commit และ push ไปยัง `main`
5. รอ GitHub Actions ทำงานจน Deploy สำเร็จ แล้วทดสอบลิงก์ดาวน์โหลดบนเว็บไซต์

> หมายเหตุ: รายการเอกสารที่แสดงอยู่ในหน้าเว็บขณะนี้เป็นรายการเตรียมไว้ ยังไม่มีไฟล์ต้นฉบับ ZIP หรือ PDF ใน Repository จึงยังไม่สามารถดาวน์โหลดเอกสารเหล่านั้นได้ ห้ามเปิดปุ่มดาวน์โหลดจนกว่าจะเพิ่มและตรวจสอบไฟล์จริงแล้ว

## การทำงานของ Workflow

Workflow ใช้ `actions/configure-pages`, `actions/upload-pages-artifact` และ `actions/deploy-pages` เพื่อเผยแพร่เนื้อหาใน Repository เป็นเว็บไซต์ GitHub Pages โดยต้องเปิด Source เป็น GitHub Actions ใน Settings > Pages ก่อน
