# FR-4 Automatic Gallery Slip Detection · สแกนสลิป

**ผู้รับผิดชอบ:** EricED
**ชุดงาน:** ชุดที่ 3

> อ่านประกอบ: หนังสือ `MindPay-FR4-Slip-Detection.pdf`

## FR นี้แก้ปัญหาอะไร

1.ผู้ใช้ไม่เสียเวลาในการสร้างบัญชีรายรับรายจ่าย
2.แก้ปัญหาลืมบันทึกรายรับรายจ่าย
3.แก้ปัญหาไม่รู้ว่าเงินหมดไปกับอะไร

## Requirement และเกณฑ์ผ่าน (Acceptance criteria)

 1.สามารถอ่านสลิปอัตโนมัติได้จากคลังรูปภาพ
 2.อ่านชื่อสลิปได้
 3.แสกนQRจากสลิปได้

## ไฟล์ที่ฉันรับผิดชอบ

| ไฟล์ | หน้าที่ (เขียนเอง 1 บรรทัด) |
|---|---|
| [`src/domain/slip.ts`](../../src/domain/slip.ts) |กำหนดโครงสร้างข้อมูลสลิปและตรรกะพื้นฐาน เช่น การตรวจวันที่ ยอดเงิน
| [`src/domain/slipNames.ts`](../../src/domain/slipNames.ts) |จัดการชื่อผู้โอน/ผู้รับในสลิป
| [`src/domain/scanQueue.ts`](../../src/domain/scanQueue.ts) |คิวรอสแกนสลิป เก็บลำดับ สถานะ และการลองใหม่
| [`src/domain/autoScan.ts`](../../src/domain/autoScan.ts) |logic สแกนอัตโนมัติ รวมถึงเงื่อนไขสแกนเฉพาะสลิปที่วันที่ตั้งแต่เวลาติดตั้งแอพเป็นต้นไป
| [`src/domain/__tests__/autoScan.test.ts`](../../src/domain/__tests__/autoScan.test.ts) |เทสต์ logic สแกนอัตโนมัติ
| [`src/domain/__tests__/slipAccuracy.test.ts`](../../src/domain/__tests__/slipAccuracy.test.ts) |เทสต์ความแม่นยำของการอ่านข้อมูลจากสลิป
| [`supabase/functions/parse-slip/index.ts`](../../supabase/functions/parse-slip/index.ts) |Edge Function ที่รับรูปสลิป อ่านข้อมูลออกมา แล้วส่งผลกลับให้แอพ
| [`supabase/functions/_shared/helpers.ts`](../../supabase/functions/_shared/helpers.ts) |ฟังก์ชันช่วยที่ใช้ร่วมกันใน Edge Functions เช่น แปลงและตรวจข้อมูลที่อ่านได้
| [`supabase/functions/_shared/common.ts`](../../supabase/functions/_shared/common.ts) |ค่าคงที่ ชนิดข้อมูล และ utility กลางของฝั่ง Edge Functions
| [`supabase/functions/_shared/__tests__/helpers.test.ts`](../../supabase/functions/_shared/__tests__/helpers.test.ts) |เทสต์ของ helpers.ts
| [`src/services/AutoScanProvider.tsx`](../../src/services/AutoScanProvider.tsx) |React Provider เก็บสถานะสแกนอัตโนมัติ แล้วแชร์ให้ทั้งแอพ
| [`src/services/useSlipScanner.ts`](../../src/services/useSlipScanner.ts) |Hook ที่หน้าจอใช้สั่งสแกนและอ่านสถานะ/ผลลัพธ์
| [`src/services/slips.ts`](../../src/services/slips.ts) |บันทึก อ่าน แก้ไข และลบสลิปในฐานข้อมูล
| [`src/services/processSlip.ts`](../../src/services/processSlip.ts) |ขั้นตอนประมวลผลสลิปหนึ่งใบ ตั้งแต่ส่งไป parse-slip จนถึงบันทึกผล
| [`src/services/gallery.ts`](../../src/services/gallery.ts) |อ่านรูปจากแกลเลอรีเครื่องบนมือถือ เพื่อหาสลิปใหม่
| [`src/services/gallery.web.ts`](../../src/services/gallery.web.ts) |เวอร์ชันของ gallery.ts สำหรับเว็บ เพราะเว็บเข้าถึงแกลเลอรีไม่ได้เหมือนมือถือ
| [`src/services/myNames.ts`](../../src/services/myNames.ts) |เก็บชื่อของผู้ใช้เอง ใช้แยกว่าสลิปเป็นรายรับหรือรายจ่าย
| [`src/app/scan.tsx`](../../src/app/scan.tsx) |หน้าจอสแกนสลิป
| [`src/app/drafts.tsx`](../../src/app/drafts.tsx) |หน้าจอรายการสลิปที่สแกนแล้วแต่ยังรอตรวจหรือยืนยัน (ฉบับร่าง)
| [`src/ui/AutoScanBanner.tsx`](../../src/ui/AutoScanBanner.tsx) |แบนเนอร์แจ้งสถานะสแกนอัตโนมัติ
| [`src/ui/ScannerStage.tsx`](../../src/ui/ScannerStage.tsx) |ส่วนแสดงภาพและความคืบหน้าระหว่างสแกน
| [`src/ui/WaitNotice.tsx`](../../src/ui/WaitNotice.tsx) |ข้อความแจ้งให้ผู้ใช้รอระหว่างประมวลผล
| [`src/ui/PeriodSummary.tsx`](../../src/ui/PeriodSummary.tsx) |สรุปยอดตามช่วงเวลา เช่น รายวัน รายเดือน

### ส่วนกลางที่ฉันดูแลเพิ่ม (ไม่ใช่ของ FR นี้โดยตรง)

- **ชุดทดสอบทั้งแอปในเบราว์เซอร์ (E2E)** (9 ไฟล์): `e2e/web-auth.mjs`, `e2e/make-slip-fixture.py`, `e2e/fixtures/photo-1.jpg`, `e2e/fixtures/photo-2.jpg`, `e2e/fixtures/photo-3.jpg`, `e2e/fixtures/slip-qr.jpg`, `e2e/fixtures/slip-qr-2.jpg`, `e2e/fixtures/slip-qr-3.jpg`, `e2e/fixtures/wallet-qr.jpg`

## ทำงานยังไง

 1.ผู้ใช้กดปุ่มสแกน (src/app/scan.tsx) หน้าจอเรียก useSlipScanner ใน src/services/useSlipScanner.ts
 2.ดึงรูปจากแกลเลอรี src/services/gallery.ts (บนเว็บใช้ gallery.web.ts) แล้วคัดเฉพาะรูปที่ถ่ายหรือบันทึกตั้งแต่เวลาติดตั้งแอพเป็นต้นไป
 3.เข้าคิว src/domain/scanQueue.ts จัดคิวรูปทีละใบ ส่วน autoScan.ts กับ AutoScanProvider.tsx ดูแลการสแกนอัตโนมัติและแสดงสถานะผ่าน AutoScanBanner.tsx
 4.ประมวลผลสลิป src/services/processSlip.ts ส่งรูปไปที่ Edge Function supabase/functions/parse-slip/index.ts ซึ่งอ่านข้อมูลจากรูปโดยใช้ _shared/helpers.ts และ _shared/common.ts
 5.แปลงและตรวจผล src/domain/slip.ts และ slipNames.ts จัดรูปข้อมูลและจับคู่ชื่อ (ร่วมกับ src/services/myNames.ts) แล้วตรวจว่าวันที่/เวลาของสลิปไม่เก่ากว่าเวลาติดตั้ง
 6.บันทึกและแสดงผล src/services/slips.ts บันทึกเป็นรายการร่าง จากนั้น drafts.tsx แสดงรายการ, ScannerStage.tsx กับ WaitNotice.tsx แสดงความคืบหน้าระหว่างรอ และ PeriodSummary.tsx สรุปยอดตามช่วงเวลา
 
## การทดสอบ

 1.src/domain/__tests__/autoScan.test.ts ตรวจลอจิกการสแกนอัตโนมัติและการคัดสลิปตามเวลาติดตั้ง
 2.src/domain/__tests__/slipAccuracy.test.ts ตรวจความแม่นยำของการอ่านข้อมูลสลิป
 3.supabase/functions/_shared/__tests__/helpers.test.ts ตรวจฟังก์ชันช่วยฝั่ง Edge Function

## ข้อจำกัดและงานต่อไป

 1.เว็บเข้าถึงแกลเลอรีไม่ได้เหมือนมือถือ
 2.ไม่อ่านสลิปเก่า
 3.ไม่อ่านสลิปที่เคยบันทึกไว้
