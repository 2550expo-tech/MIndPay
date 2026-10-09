# FR-6 Money Runway · เงินพอถึง

**ผู้รับผิดชอบ:** ✏️ ชื่อ-นามสกุล (@GitHub-username)
**ชุดงาน:** ชุดที่ 5

> ✏️ = ช่องที่ต้องเขียนเองด้วยคำของตัวเอง ลบเครื่องหมาย ✏️ ออกเมื่อเขียนเสร็จ
> อ่านประกอบ: หนังสือ `MindPay-FR6-Money-Runway.pdf`

## FR นี้แก้ปัญหาอะไร

✏️ 3–5 บรรทัด: ผู้ใช้เจอปัญหาอะไร และ FR นี้ช่วยได้ยังไง

## Requirement และเกณฑ์ผ่าน (Acceptance criteria)

✏️ เขียนเป็นข้อ ๆ ว่าต้องทำอะไรได้บ้างจึงถือว่า FR นี้ผ่าน

## ไฟล์ที่ฉันรับผิดชอบ

| ไฟล์ | หน้าที่ (เขียนเอง 1 บรรทัด) |
|---|---|
| [`src/domain/runway.ts`](../../src/domain/runway.ts) | ✏️ |
| [`src/domain/goals.ts`](../../src/domain/goals.ts) | ✏️ |
| [`src/domain/__tests__/goals.test.ts`](../../src/domain/__tests__/goals.test.ts) | ✏️ |
| [`src/app/(tabs)/runway.tsx`](../../src/app/%28tabs%29/runway.tsx) | ✏️ |
| [`src/app/goals.tsx`](../../src/app/goals.tsx) | ✏️ |
| [`src/app/goal.tsx`](../../src/app/goal.tsx) | ✏️ |
| [`src/ui/Slider.tsx`](../../src/ui/Slider.tsx) | ✏️ |
| [`src/ui/Jar.tsx`](../../src/ui/Jar.tsx) | ✏️ |
| [`src/ui/art.tsx`](../../src/ui/art.tsx) | ✏️ |
| [`supabase/migrations/20260929000000_savings_goals.sql`](../../supabase/migrations/20260929000000_savings_goals.sql) | ✏️ |

### ส่วนกลางที่ฉันดูแลเพิ่ม (ไม่ใช่ของ FR นี้โดยตรง)

- **ชุดเทสต์รวมของแอป** (1 ไฟล์): `src/domain/__tests__/domain.test.ts`
- **โครงแอป: เมนูหลัก ตั้งค่า เหรียญ และมีอะไรใหม่** (14 ไฟล์): `src/app/_layout.tsx`, `src/app/(tabs)/_layout.tsx`, `src/app/settings.tsx`, `src/app/whatsnew.tsx`, `src/app/achievements.tsx`, `src/services/whatsNew.ts`, `src/services/useAchievements.ts`, `src/data/prefs.ts`, `src/domain/sample.ts`, `src/domain/achievements.ts`, `src/domain/__tests__/sample.test.ts`, `src/domain/__tests__/achievements.test.ts`, `src/ui/UpdateBanner.tsx`, `src/ui/Medal.tsx`
- **ตั้งค่าโปรเจกต์ CI ไอคอน และเอกสาร** (33 ไฟล์): `package.json`, `package-lock.json`, `tsconfig.json`, `eslint.config.js`, `vitest.config.ts`, `app.json`, `app.config.js`, `eas.json`, `.env.example`, `.claude/settings.json`, `AGENTS.md`, `CLAUDE.md`, `README.md`, `.github/workflows/web.yml`, `.github/workflows/e2e-webkit.yml`, `.github/workflows/android-apk.yml`, `.github/workflows/eas-update.yml`, `scripts/make_icons.py`, `scripts/theme-shot.mjs`, `scripts/web-home-screen.mjs`, `e2e/demo-video.mjs`, `e2e/fake-backend.mjs`, `docs/AI_USAGE_LOG.md`, `docs/TRACEABILITY.md`, `assets/android-icon-background.png`, `assets/android-icon-foreground.png`, `assets/android-icon-monochrome.png`, `assets/favicon.png`, `assets/icon.png`, `assets/splash-icon.png`, `assets/web/apple-touch-icon.png`, `assets/web/icon-192.png`, `assets/web/icon-512.png`

## ทำงานยังไง

✏️ เล่าตั้งแต่ผู้ใช้กดปุ่ม จนถึงเห็นผลบนจอ ว่าข้อมูลผ่านไฟล์ไหนบ้าง

## การทดสอบ

✏️ เทสต์ไหนตรวจอะไร และรันยังไง (เช่น `npm test`)

## ข้อจำกัดและงานต่อไป

✏️ สิ่งที่ยังไม่ดี และสิ่งที่อยากทำต่อ (ดูไอเดียได้จากบท "ข้อจำกัด" ในหนังสือ)
