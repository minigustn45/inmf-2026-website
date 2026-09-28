# 2026 국제 해군 군수 및 MRO 협력 포럼 (INMF 2026)
International Naval Logistics & MRO Cooperation Forum — 공식 웹사이트

## 프로젝트 구조

이 사이트는 별도의 빌드 도구 없이 동작하는 **단일 정적 HTML 파일**입니다.

```
index.html   # 전체 페이지 (마크업 뼈대 + 인라인 CSS + 인라인 JS)
```

- `<head>` 안 `<style>` 블록에 전체 CSS가 포함되어 있습니다.
- `<body>`는 `#gnb`(헤더), `#app`(본문), `#foot`(푸터)의 빈 컨테이너만 가지고 있고,
  실제 콘텐츠는 하단 `<script>` 블록의 JavaScript가 템플릿 리터럴로 생성해
  런타임에 DOM에 렌더링합니다(클라이언트 사이드 라우팅 포함, `route()`).
- 이미지(키비주얼, 부스 배치도, 후원사 로고 등)는 `data:image/webp;base64,...`
  형태로 파일 내부에 인라인 포함되어 있어 추가 이미지 파일이 필요 없습니다.
- 폰트는 Google Fonts(Black Han Sans, IBM Plex Sans KR, Montserrat)를
  `<link>`로 외부 로드합니다.
- 외부 JS 라이브러리 의존성 없음 (순수 바닐라 JS).

## 로컬 실행 방법

빌드 과정이 없으므로 정적 파일 서버로 바로 실행할 수 있습니다.

```bash
# 예시 1: Python
python3 -m http.server 8000
# 브라우저에서 http://localhost:8000/index.html 접속

# 예시 2: Node (npx serve)
npx serve .
```

또는 `index.html` 파일을 브라우저에서 직접 열어도 대부분의 기능이 동작합니다
(단, `file://` 프로토콜에서는 일부 브라우저 정책으로 제한이 있을 수 있으므로
로컬 서버 실행을 권장합니다).

## 검사

- `node --check`로 인라인 스크립트 문법 검증 완료.
- 로컬 정적 서버로 서빙 시 200 응답 및 파일 무결성 확인 완료.
