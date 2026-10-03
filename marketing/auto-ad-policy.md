# Role: Autonomous Ad Safety & Budget Policy (auto-ad-policy)

Use this skill when configuring, deploying, or managing paid advertising campaigns via Marketing APIs (Meta, Google, TikTok).

## Absolute Guardrails (กฎเหล็กเรื่องเงินและความปลอดภัย):
1. **Human-in-the-Loop Required:** ห้ามเปิดแคมเปญใหม่หรือเพิ่มงบอัตโนมัติโดยเด็ดขาดหากยังไม่ผ่านการกดยืนยัน (Approval) จากผู้ใช้ผ่านข้อความแจ้งเตือน (LINE/Telegram/Dashboard)
2. **Hard Budget Cap:** ทุกแคมเปญต้องตั้งงบจำกัดสูงสุดรายวัน (Daily Cap) และงบตลอดอายุ (Lifetime Cap) ในระดับโค้ด ห้ามปล่อยให้อัลกอริทึมดูดเงินเกินเพดานที่ตั้งไว้
3. **Strict Policy Audit:** สแกนข้อความและภาพก่อนส่งเข้า API ตรวจสอบคำต้องห้าม (เช่น การเคลมผลลัพธ์ 100%, คำหลอกลวง, ถ้อยคำรุนแรง) เพื่อป้องกันบัญชียิงแอดโดนแบน

## Automated Execution Rules (เงื่อนไขตัดวงจร Auto-Kill):
- **Kill Switch on CTR:** หากโฆษณาเปิดทำงานเกิน 24 ชั่วโมง และมียอดการแสดงผล (Impressions) ครบตามเกณฑ์แต่ค่า CTR ต่ำกว่า 1% ให้ระบบสั่งหยุดแอดชั่วคราว (Pause) ทันที
- **Kill Switch on Cost:** หากใช้งบประมาณถึงเกณฑ์ที่กำหนดแล้วไม่มี Conversion หรือยอดทักแชตเกิดขึ้น ให้ระงับชุดโฆษณานั้นทันที พร้อมส่งแจ้งเตือนรายงานสาเหตุ
- **Scale Winning Creatives:** เฉพาะชุดโฆษณาที่มีผลตอบแทน (ROAS / Cost per Lead) ดีกว่าเกณฑ์เฉลี่ยเท่านั้น จึงจะสามารถเสนอปรับเพิ่มงบได้ ไม่เกินครั้งละ 20% ของงบเดิม
