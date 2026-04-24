---
name: 프로젝트 기술 스택 및 아키텍처
description: claude-nextjs-starters 프로젝트의 핵심 기술 스택, 파일 구조, 주요 패턴 요약
type: project
---

**스택**: Next.js 16.2.4 (App Router) · React 19.2.4 · TypeScript(strict) · TailwindCSS v4 · ShadcnUI (radix-nova 스타일)

**핵심 파일 구조**:
- `app/layout.tsx` — RootLayout, 폰트(Geist/Geist_Mono), ThemeProvider 래핑
- `app/page.tsx` — 랜딩 페이지 (Server Component, 클라이언트 상태 없음)
- `app/globals.css` — @import "tailwindcss", @theme inline 블록으로 CSS 변수 관리, @custom-variant dark
- `components/theme/theme-provider.tsx` — 커스텀 ThemeProvider (localStorage + .dark 클래스 토글), "use client"
- `components/theme/theme-toggle.tsx` — Sun/Moon 아이콘 토글 버튼, "use client"
- `components/layout/header.tsx` — Server Component (ThemeToggle만 client)
- `components/layout/footer.tsx` — Server Component
- `components/ui/button.tsx` — CVA 기반, Slot.Root(radix-ui 통합 패키지) 사용
- `components/ui/card.tsx` — 함수형 선언, cn() 사용
- `components/ui/badge.tsx` — CVA 기반
- `lib/utils.ts` — cn() (clsx + tailwind-merge)

**주요 패턴**:
- UI 컴포넌트: `cva()` + `cn()` 조합
- Slot: `import { Slot } from "radix-ui"` → `Slot.Root`
- 테마: next-themes 미사용, localStorage 기반 커스텀 구현
- 경로 별칭: `@/*` → 프로젝트 루트

**Why**: 스타터킷 프로젝트로 환경 설정 없이 바로 개발 시작이 목표

**How to apply**: 코드 리뷰 시 이 패턴을 기준으로 일관성 평가
