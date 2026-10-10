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
| [`src/domain/slip.ts`](../../src/domain/slip.ts) |
| [`src/domain/slipNames.ts`](../../src/domain/slipNames.ts) |
| [`src/domain/scanQueue.ts`](../../src/domain/scanQueue.ts) |
| [`src/domain/autoScan.ts`](../../src/domain/autoScan.ts) |
| [`src/domain/__tests__/autoScan.test.ts`](../../src/domain/__tests__/autoScan.test.ts) |
| [`src/domain/__tests__/slipAccuracy.test.ts`](../../src/domain/__tests__/slipAccuracy.test.ts) |
| [`supabase/functions/parse-slip/index.ts`](../../supabase/functions/parse-slip/index.ts) |
| [`supabase/functions/_shared/helpers.ts`](../../supabase/functions/_shared/helpers.ts) |
| [`supabase/functions/_shared/common.ts`](../../supabase/functions/_shared/common.ts) |
| [`supabase/functions/_shared/__tests__/helpers.test.ts`](../../supabase/functions/_shared/__tests__/helpers.test.ts) |
| [`src/services/AutoScanProvider.tsx`](../../src/services/AutoScanProvider.tsx) |
| [`src/services/useSlipScanner.ts`](../../src/services/useSlipScanner.ts) |
| [`src/services/slips.ts`](../../src/services/slips.ts) |
| [`src/services/processSlip.ts`](../../src/services/processSlip.ts) |
| [`src/services/gallery.ts`](../../src/services/gallery.ts) |
| [`src/services/gallery.web.ts`](../../src/services/gallery.web.ts) |
| [`src/services/myNames.ts`](../../src/services/myNames.ts) |
| [`src/app/scan.tsx`](../../src/app/scan.tsx) |
| [`src/app/drafts.tsx`](../../src/app/drafts.tsx) |
| [`src/ui/AutoScanBanner.tsx`](../../src/ui/AutoScanBanner.tsx) |
| [`src/ui/ScannerStage.tsx`](../../src/ui/ScannerStage.tsx) |
| [`src/ui/WaitNotice.tsx`](../../src/ui/WaitNotice.tsx) |
| [`src/ui/PeriodSummary.tsx`](../../src/ui/PeriodSummary.tsx) |

### ส่วนกลางที่ฉันดูแลเพิ่ม (ไม่ใช่ของ FR นี้โดยตรง)

- **ชุดทดสอบทั้งแอปในเบราว์เซอร์ (E2E)** (9 ไฟล์): `e2e/web-auth.mjs`, `e2e/make-slip-fixture.py`, `e2e/fixtures/photo-1.jpg`, `e2e/fixtures/photo-2.jpg`, `e2e/fixtures/photo-3.jpg`, `e2e/fixtures/slip-qr.jpg`, `e2e/fixtures/slip-qr-2.jpg`, `e2e/fixtures/slip-qr-3.jpg`, `e2e/fixtures/wallet-qr.jpg`

## ทำงานยังไง

 เมื่อมีสลิปถูกเพิ่มเข้ามาในคลังรูปภาพ -> ระบบอ่านเองอัตโนมัติ -> บันทึกลงในแอป

## การทดสอบ

 เทสต์ไหนตรวจอะไร และรันยังไง (เช่น `npm test`)

## ข้อจำกัดและงานต่อไป

 1.ไม่อ่านสลิปเก่า
 2.ไม่อ่านสลิปที่เคยบันทึกไว้
