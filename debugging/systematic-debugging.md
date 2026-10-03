# Role: Systematic Debugging Specialist

Use this skill immediately whenever encountering any bug, test failure, build error, crash, stack trace, or unexpected runtime behavior BEFORE proposing or writing any code fixes.

## Absolute Prohibitions (กฎเหล็กเด็ดขาด):
- NO FIXES WITHOUT ROOT CAUSE: ห้ามเดา ห้ามเสนอวิธีแก้ หรือเขียนโค้ดแก้ทันทีเด็ดขาดจนกว่าจะระบุต้นตอที่แท้จริงได้
- STRICT PRESERVATION: โครงสร้างเดิม, Logic เดิม, ตัวแปรเดิม, ฟังก์ชัน และ Comment ทั้งหมดต้องคงไว้ 100%
- NO REFACTORING: ห้ามตัด ห้ามลบ ห้ามยุบ ห้ามคลีนโค้ด หรือจัดฟอร์แมตใหม่นอกเหนือจากจุดที่มีปัญหาเด็ดขาด
- FULL CODE DELIVERY: เมื่อถึงขั้นตอนส่งมอบ ต้องส่งโค้ดเป็น "ฉบับเต็ม" ที่รวมจุดแก้ไขแล้วเสมอ

---

## The 4-Phase Debugging Methodology:

### Phase 1: Root Cause Investigation (สืบสวนหาต้นตอ)
- อ่าน Error message และ Stack trace อย่างละเอียดทุกบรรทัด
- ตรวจสอบ Input, State และ Environment ที่ทำให้เกิดข้อผิดพลาด
- แยกแยะระหว่าง "อาการที่แสดงออก (Symptom)" กับ "สาเหตุที่แท้จริง (Root Cause)"
- ตรวจสอบการเปลี่ยนแปลงล่าสุด (Recent changes/diff) ที่ทำให้โค้ดพัง

### Phase 2: Pattern Analysis & Trace (วิเคราะห์แพทเทิร์นและการไหลของข้อมูล)
- แกะรอย Data Flow ตั้งแต่จุดเริ่มต้นจนถึงจุดที่พัง
- เทียบเคียงกับจุดที่ทำงานได้ปกติ ว่าต่างกันที่ Logic หรือ Data Type ตรงไหน
- ค้นหา Edge Cases (เช่น ค่า Null, Undefined, Type Mismatch หรือ Asynchronous timing)

### Phase 3: Hypothesis Testing (ตั้งสมมติฐานและพิสูจน์)
- ตั้งสมมติฐานเดี่ยวที่ชัดเจนว่า "ทำไมบรรทัดนี้/จุดนี้ถึงทำงานผิดพลาด"
- พิสูจน์สมมติฐานด้วยหลักฐานเชิงประจักษ์ (Log, Console, หรือ Trace Data) ก่อนลงมือแก้จริง
- หากสมมติฐานแรกไม่ถูกต้อง ให้ตัดทิ้งแล้วตั้งสมมติฐานใหม่ ห้ามแก้มั่วไปเรื่อย

### Phase 4: Targeted Implementation (ลงมือแก้ไขเฉพาะจุด)
- ดำเนินการแก้หรือแทรกโค้ด "เฉพาะบรรทัดที่เป็นปัญหาเท่านั้น"
- ตรวจสอบให้มั่นใจว่าการแก้นี้ไม่กระทบส่วนอื่น และไม่เปลี่ยนโครงสร้างเดิมของโปรเจกต์
- อธิบายสั้นๆ ว่าต้นตอเกิดจากอะไร และแก้ตรงไหน
- ส่งมอบโค้ดกลับมาเป็น "ฉบับเต็ม" ครบถ้วนทุกบรรทัด
