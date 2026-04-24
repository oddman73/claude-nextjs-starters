---
name: 반복 발견 이슈 패턴
description: 이 프로젝트에서 초기 리뷰 시 발견된 반복 가능성 높은 이슈 패턴
type: feedback
---

**패턴 1: ThemeProvider system 테마 깜빡임(FOUC)**
- system 테마 초기값이 "system"이지만, localStorage 읽기 전까지 서버 렌더링과 불일치 발생 가능
- suppressHydrationWarning이 html에 있어 일부 완화되나, ThemeProvider 내부에서 초기 렌더시 깜빡임 발생 가능
- Why: useEffect는 마운트 이후 실행되므로 첫 렌더 시 테마가 결정되지 않은 상태
- How to apply: ThemeProvider 검토 시 초기 렌더 전 테마 결정 로직 확인

**패턴 2: 외부 링크 rel 속성 누락**
- target="_blank" 사용 시 rel="noopener noreferrer" 누락 케이스 빈번
- footer.tsx의 GitHub 링크가 rel 속성 없이 target="_blank" 사용
- How to apply: 외부 링크 리뷰 시 반드시 rel 속성 확인

**패턴 3: 데코레이티브 아이콘 aria-hidden 누락**
- lucide-react 아이콘을 장식 목적으로 사용할 때 aria-hidden="true" 미적용
- 스크린 리더가 불필요한 아이콘 이름을 읽어 접근성 저하
- How to apply: 아이콘 사용 컴포넌트 리뷰 시 의미 있는 아이콘 vs 장식용 아이콘 구분 확인

**패턴 4: ThemeToggle system 테마 전환 미지원**
- system → dark 또는 system → light로 첫 클릭 시 올바르게 동작하지 않을 수 있음
- theme === "system"일 때 toggle이 "light"로 전환(dark !== "dark")
- How to apply: 테마 토글 로직 리뷰 시 system 상태 처리 확인
