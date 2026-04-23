주어진 라우트명으로 Next.js App Router 페이지를 생성해주세요.

라우트명: $ARGUMENTS

## 생성할 파일

### 1. `app/$ARGUMENTS/page.tsx`

아래 패턴으로 생성:
- `export default function` 페이지 컴포넌트 (라우트명을 PascalCase로 변환하여 컴포넌트명 사용)
- `export const metadata: Metadata` 를 상단에 포함 (title, description 한국어로)
- 최상위 `<div className="flex flex-col">` 래퍼
- Hero 섹션: 페이지 제목(`<h1>`)과 설명(`<p className="text-muted-foreground">`) 포함
- `container mx-auto max-w-6xl px-4 py-16` 레이아웃 클래스 사용
- `import type { Metadata } from "next"` 포함

### 2. `app/$ARGUMENTS/loading.tsx`

아래 패턴으로 생성:
- `Skeleton` 컴포넌트 사용: `import { Skeleton } from "@/components/ui/skeleton"`
- Hero 섹션과 콘텐츠 영역의 스켈레톤 레이아웃 구성
- 실제 page.tsx의 레이아웃 구조와 유사하게 구성

## 주의사항
- TailwindCSS v4 CSS 변수 기반 색상 사용 (`text-muted-foreground`, `bg-background` 등)
- 다크모드는 별도 클래스 불필요 (CSS 변수가 자동 처리)
- `cn()` 유틸리티는 조건부 클래스 조합 시에만 사용
- Header/Footer는 layout.tsx에서 이미 처리하므로 포함하지 않음
- ShadcnUI 컴포넌트(`Card`, `Badge`, `Button` 등)를 자유롭게 활용

파일 생성 후 생성된 파일 경로 2개를 알려주세요.
