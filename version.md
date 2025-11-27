# KAHIS EMR (Vue.js Version) - VERSION.MD

## BETA 1.0 VERSION (Vue.js Migration & Full Order Rx)
(พฤศจิกายน 2025)

### วัตถุประสงค์ (Objective)
ยกระดับโครงสร้างซอฟต์แวร์ (Re-platforming) จาก Vanilla JS สู่ **Vue.js 3 + Vite** เพื่อความทันสมัย ดูแลรักษาง่าย และมีประสิทธิภาพสูง พร้อมทั้งเปิดตัวโมดูล **Order Rx** รูปแบบใหม่ที่สมบูรณ์แบบ

### สิ่งที่อัพเดท (Updates)

#### 1. Core Architecture (โครงสร้างหลัก)
* **Framework:** เปลี่ยนมาใช้ **Vue.js 3 (Composition API)** เต็มรูปแบบ
* **Styling:** ใช้ **Bulma CSS** ร่วมกับ SASS Variables เพื่อจัดการ Theme (Standard / Earth Tone)
* **State Management:** ใช้ **Pinia** ในการจัดการข้อมูลกลาง (Patient, Rx Cart, Tx Cart) แทน Global Variables
* **Routing:** ใช้ **Vue Router** ในการเปลี่ยนหน้า (SPA) แทนการโหลดไฟล์ HTML
* **Icons:** เปลี่ยนมาใช้ **Lucide Vue Next** เพื่อประสิทธิภาพและการแสดงผลที่คมชัด

#### 2. User Interface (UI Layout)
* **Dynamic Layout:** ระบบซ่อน/แสดงแถบข้อมูลผู้ป่วย (Patient Banner) และเมนูสั่งงาน (Tab Menu) อัตโนมัติตามสถานะการเลือกผู้ป่วย
* **Responsive NavBar:** เมนูบาร์ด้านบนรองรับการใช้งานบนมือถือ (Hamburger Menu)
* **Sticky Elements:** เมนูและแถบเครื่องมือต่างๆ ถูกตั้งค่าให้ลอยติดขอบจอ (Sticky) เพื่อความสะดวกในการใช้งาน

#### 3. Module: Order Rx (ระบบสั่งยา)
* **3-Column Dashboard:** จัดหน้าจอเป็น 3 ส่วน (หมวดหมู่ / รายการยา / ตะกร้าสินค้า) ที่เลื่อนดูข้อมูลได้อิสระ
* **Dual Language Support:** รองรับฉลากยา 2 ภาษา (ไทย/อังกฤษ) สามารถสลับและดึงค่า Default มาแก้ไขได้ทันที
* **Smart Cart:**
    * แสดงรายการยาพร้อม Tag บรรจุภัณฑ์ (Container) และหน่วยนับ (Unit) ที่ชัดเจน
    * สามารถแก้ไขข้อความฉลาก (Label) ได้โดยตรงในตะกร้า
* **Virtual Numpad:** ระบบแป้นตัวเลขจำลองบนหน้าจอ สำหรับกรอกจำนวนยา (รองรับ Touch Screen)
* **Enhanced Meta Data:** ย้ายส่วนบันทึกเพิ่มเติม (Order Note, Pharmacy Note) และการระบุแพทย์/เวลา ลงมาเป็นสัดส่วนที่ชัดเจนด้านล่าง

### รายละเอียดทางเทคนิค (Implementation Details)
* **`src/stores/useRxStore.js`:** คลังข้อมูลยา รองรับฟิลด์ `default_label_th`, `default_label_en`
* **`src/components/modules/OrderRx.vue`:** หน้าจอสั่งยาหลัก ที่รวม Logic การค้นหา, การเลือกภาษา, และการจัดการตะกร้าไว้ด้วยกัน
* **`src/components/common/VirtualNumpad.vue`:** Component แป้นตัวเลขกลางที่นำไปใช้ซ้ำได้
* **`src/components/layout/PatientBanner.vue`:** แถบข้อมูลผู้ป่วยที่ใช้ Flexbox จัด Layout ให้ข้อมูลไม่ซ้อนทับกัน