# FR-5 AI Coach · โค้ชน้องกล้า

**ผู้รับผิดชอบ:** ✏️ ชื่อ-นามสกุล (@GitHub-username)
**ชุดงาน:** ชุดที่ 4

> ✏️ = ช่องที่ต้องเขียนเองด้วยคำของตัวเอง ลบเครื่องหมาย ✏️ ออกเมื่อเขียนเสร็จ
> อ่านประกอบ: หนังสือ `MindPay-FR5-AI-Coach.pdf`

## FR นี้แก้ปัญหาอะไร

✏️ 3–5 บรรทัด: ผู้ใช้เจอปัญหาอะไร และ FR นี้ช่วยได้ยังไง

## Requirement และเกณฑ์ผ่าน (Acceptance criteria)

✏️ เขียนเป็นข้อ ๆ ว่าต้องทำอะไรได้บ้างจึงถือว่า FR นี้ผ่าน

## ไฟล์ที่ฉันรับผิดชอบ

| ไฟล์ | หน้าที่ (เขียนเอง 1 บรรทัด) |
|---|---|
| [`src/domain/insights.ts`](../../src/domain/insights.ts) | ✏️ |
| [`src/domain/buddy.ts`](../../src/domain/buddy.ts) | ✏️ |
| [`src/domain/klaTalk.ts`](../../src/domain/klaTalk.ts) | ✏️ |
| [`src/domain/price.ts`](../../src/domain/price.ts) | ✏️ |
| [`src/domain/__tests__/buddy.test.ts`](../../src/domain/__tests__/buddy.test.ts) | ✏️ |
| [`src/domain/__tests__/klaTalk.test.ts`](../../src/domain/__tests__/klaTalk.test.ts) | ✏️ |
| [`supabase/functions/coach/index.ts`](../../supabase/functions/coach/index.ts) | ✏️ |
| [`supabase/migrations/20261001000000_atomic_ai_quota.sql`](../../supabase/migrations/20261001000000_atomic_ai_quota.sql) | ✏️ |
| [`src/services/coach.ts`](../../src/services/coach.ts) | ✏️ |
| [`src/services/tts.ts`](../../src/services/tts.ts) | ✏️ |
| [`src/services/tts.web.ts`](../../src/services/tts.web.ts) | ✏️ |
| [`src/app/(tabs)/coach.tsx`](../../src/app/%28tabs%29/coach.tsx) | ✏️ |
| [`src/ui/kla/KlaStage.tsx`](../../src/ui/kla/KlaStage.tsx) | ✏️ |
| [`src/ui/kla/KlaBackdrop.tsx`](../../src/ui/kla/KlaBackdrop.tsx) | ✏️ |
| [`src/ui/kla/KlaPicture.tsx`](../../src/ui/kla/KlaPicture.tsx) | ✏️ |
| [`src/ui/kla/art.tsx`](../../src/ui/kla/art.tsx) | ✏️ |
| [`src/ui/kla/useKlaTalk.ts`](../../src/ui/kla/useKlaTalk.ts) | ✏️ |
| [`src/ui/Buddy.tsx`](../../src/ui/Buddy.tsx) | ✏️ |

### ส่วนกลางที่ฉันดูแลเพิ่ม (ไม่ใช่ของ FR นี้โดยตรง)

- **ตู้สกิน ภารกิจ และธีมฮาโลวีน** (14 ไฟล์): `src/domain/skins.ts`, `src/domain/missions.ts`, `src/domain/halloween.ts`, `src/domain/__tests__/skins.test.ts`, `src/domain/__tests__/missions.test.ts`, `src/domain/__tests__/halloween.test.ts`, `src/services/kla.ts`, `src/app/skins.tsx`, `src/ui/halloween.tsx`, `scripts/kla-icons/finish.py`, `scripts/kla-icons/make.mjs`, `scripts/kla-icons/pictures.tsx`, `scripts/kla-icons/react-dom-server.d.ts`, `scripts/kla-icons/svg-shim.tsx`

## ทำงานยังไง

✏️ เล่าตั้งแต่ผู้ใช้กดปุ่ม จนถึงเห็นผลบนจอ ว่าข้อมูลผ่านไฟล์ไหนบ้าง

## การทดสอบ

✏️ เทสต์ไหนตรวจอะไร และรันยังไง (เช่น `npm test`)

## ข้อจำกัดและงานต่อไป

✏️ สิ่งที่ยังไม่ดี และสิ่งที่อยากทำต่อ (ดูไอเดียได้จากบท "ข้อจำกัด" ในหนังสือ)
