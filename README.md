# 타임템플릿 랜딩 페이지

> 타임템플릿(Time Template) 모바일 앱 공식 랜딩 페이지

![Live](https://img.shields.io/badge/Live-mincoln419.github.io%2Ftime__template-A8BFA6?style=flat-square)
![Static Site](https://img.shields.io/badge/Static-HTML%20%2B%20CSS%20%2B%20JS-44474B?style=flat-square)
![GitHub Pages](https://img.shields.io/badge/GitHub_Pages-Deployed-5E7A64?style=flat-square)

---

## 🌐 라이브 사이트

**<https://mincoln419.github.io/time_template/>**

이 레포지토리는 타임템플릿 앱 자체가 아니라, 앱을 소개하는 **정적 랜딩 페이지**입니다.
실제 앱 코드는 별도 레포지토리에서 관리됩니다.

---

## 🧱 스택

- **HTML / CSS / JavaScript** (Vanilla, 빌드 도구 없음)
- **디자인 토큰 시스템** — CSS Custom Properties 기반 (`colors_and_type.css`)
- **Lucide Icons** — CDN
- **Google Fonts** — Noto Sans KR
- **Jekyll** — GitHub Pages 호환 메타데이터(`_config.yml`)
- **GitHub Actions** — `peaceiris/actions-gh-pages` 자동 배포

---

## 📁 디렉토리 구조

```
time_template/
├── index.html              # 랜딩 페이지 본문
├── privacy.html            # 개인정보처리방침
├── terms.html              # 이용약관
├── colors_and_type.css     # 디자인 토큰 (컬러/타입/스페이싱/그림자)
├── landing.css             # 랜딩 페이지 컴포넌트 스타일
├── _config.yml             # Jekyll/SEO 설정
├── _redirects              # GitHub Pages 리다이렉트
├── package.json            # 로컬 미리보기용 (http-server)
├── LICENSE                 # MIT
├── assets/
│   ├── icon.png            # favicon
│   ├── logo.jpg            # 헤더 로고
│   └── screens/            # 앱 스크린샷 (OG 이미지 포함)
└── .github/workflows/
    └── deploy.yml          # main 푸시 시 자동 배포
```

---

## 💻 로컬 미리보기

```bash
npm install
npm start          # http-server -p 8080 (브라우저 자동 오픈)
```

`http://localhost:8080`에서 확인 가능합니다.

---

## ✏️ 컨텐츠 수정 가이드

### 1) 카피(문구) 수정 — KO/EN 동시
`index.html` 하단의 `<script>` 블록 안 `dict` 객체를 수정합니다.

```js
"hero.h1": { ko: "하루를<br>디자인하다.", en: "Design<br>your day." }
```

페이지의 모든 텍스트는 `data-i18n` 키로 묶여 있고, 사용자가 KO/EN 토글 시
이 사전에서 값을 가져와 교체됩니다. 선택한 언어는 `localStorage`에 저장됩니다.

### 2) 앱 스크린샷 교체 (한/영 별도)
`assets/screens/ko/` (한국어), `assets/screens/en/` (영어) 폴더에 동일한 파일명으로 4개씩 배치합니다.
- `03-templates-list.jpg` — 템플릿 섹션
- `06-journal-morning.jpg`, `07-journal-evening.jpg` — 일기 섹션
- `09-home-radial.jpg` — Hero + OG 이미지

영문 이미지가 없는 경우 자동으로 한국어 이미지로 fallback 됩니다 (`img.onerror`). 영어 화면 캡처 가능 시 `assets/screens/en/`에 동일 파일명으로 올리면 토글 시 자동 표시.

### 3) 디자인 토큰(컬러/타입) 수정
`colors_and_type.css` 의 `:root` 변수만 바꾸면 모든 페이지에 일괄 반영됩니다.
- 브랜드 컬러: `--sage-500`, `--sage-700`, `--cream-100`
- 카테고리 컬러: `--cat-sleep`, `--cat-physical` 등 7종
- 텍스트 컬러: `--ink-900` ~ `--ink-300`

### 4) 법적 페이지 (`privacy.html` / `terms.html`)
법조항 본문만 수정하세요. 스타일은 `colors_and_type.css` 토큰을 공유합니다.

---

## 🚀 배포

`main` 브랜치에 푸시되면 GitHub Actions가 자동으로 GitHub Pages에 배포합니다.

```
dev (작업) ──[단계별 커밋]──> dev push ──> dev→main 머지 ──> main push ──> GH Pages 배포
```

워크플로: `.github/workflows/deploy.yml`

---

## 🌿 브랜치 컨벤션

- `dev` — 작업 브랜치 (커밋이 누적되는 곳)
- `main` — 운영 브랜치 (GH Pages 배포 트리거)

대규모 변경은 `dev`에 **변경 단위별로 커밋을 분리**한 뒤, 일괄 `dev → main` 머지로 배포합니다.

---

## 📄 라이선스

[MIT License](LICENSE) — © 2024 CodeNYang (원작자 표기 유지)

---

## 🙋 문의

[GitHub Issues](https://github.com/mincoln419/time_template/issues)
