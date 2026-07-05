# 시흥 누수탐지 - 원케어 배관 정적 홈페이지 (Cloudflare Pages 배포용)

네이버에서 `시흥 누수탐지` 검색 시 상위 노출을 목표로 지역 SEO 최적화를 진행한 정적 랜딩페이지입니다.
허위 정보·스팸성 키워드 반복 없이, 실제 방문자가 읽고 신뢰할 수 있는 콘텐츠와 정석적인 구조화 데이터로 구성했습니다.

## 파일 구조

```
/
├─ index.html      (메인 페이지, 시흥 누수탐지 중심 SEO 구조 적용)
├─ 404.html        (없는 경로 접근 시 표시되는 페이지, noindex)
├─ robots.txt
├─ sitemap.xml
├─ _headers        (보안 헤더 + 캐시 설정)
├─ _redirects
├─ title.png       (링크 공유 전용 대표 이미지, 본문에는 사용 안 함)
├─ images/         (본문 하단 "작업 사례 예시" 섹션에 사용되는 실제 현장 사진)
└─ README.md
```

## 이번 SEO 작업 요약

### 1. `<head>` 메타 최적화
- **title**: `시흥 누수탐지 | 원케어 배관 24시 상담` — "시흥 누수탐지"로 시작, 20자 내외
- **description**: 키워드 나열 대신 자연스러운 문장으로 작성 (수도·화장실·천장·배관 누수 진단 + 지역명 + 상담 유도)
- **robots**: `index, follow` 유지
- **canonical / OG / Twitter**: 모두 `시흥 누수탐지` 중심 문구로 통일, 이미지는 `title.png` 절대경로 사용
- 네이버/구글 소유확인 메타태그는 그대로 유지 (실제 코드만 나중에 입력)

### 2. H 태그 구조
- `h1`은 페이지에 **1개만** 사용 — 히어로 섹션의 `시흥 누수탐지, 원인부터 정확하게 진단합니다`
- 헤더/푸터의 로고 텍스트는 `h1`이 중복되지 않도록 `<p>` 태그로 변경
- `h2` 9개: 전문 서비스 / 수도·화장실·천장 누수 진단 / 발생 원인 / 장비와 작업 과정 / 비용 안내 / 전지역 상담 / FAQ / 작업 사례 예시 / 상담 문의
- 각 섹션 세부 항목은 모두 `h3`로 통일 (기존 h4·h5 혼용을 정리)

### 3. 신규 본문 섹션 (콘텐츠 보강)
- `#diagnosis` 시흥 수도·화장실·천장 누수 진단 — 증상별 차이를 설명하는 3개 카드
- `#causes` 시흥에서 누수가 자주 발생하는 원인 — 노후 배관, 방수층 손상, 보일러 난방 배관, 아랫집 천장 누수 확인법
- `#process`(기존 섹션 보강) 청음식 탐지·열화상 카메라·배관 압력 테스트 등 장비 설명, 추측 공사와의 차이, 공사 범위 안내 문구 추가
- `#areas` 시흥 전지역 빠른 상담 가능 — 정왕동, 배곧, 은행동, 대야동, 목감동, 월곶동, 장현동, 능곡동, 신천동, 매화동, 연성동을 자연스러운 문장 + 배지(chips)로 노출
- `#faq` 시흥 누수탐지 자주 묻는 질문 — 본문 FAQ와 JSON-LD `FAQPage`가 동일한 5개 질문/답변으로 일치
- 헤더 아래 시각적 Breadcrumb(`홈 / 시흥 누수탐지`) 추가 — JSON-LD `BreadcrumbList`와 동일한 구조

### 4. 이미지 SEO
- `#cases` "작업 사례 예시" 섹션의 이미지 10장 `alt`를 모두 다르게 작성 (시흥 누수탐지, 화장실 누수, 천장 누수, 배관 누수, 수도 누수, 누수 공사 등 키워드를 자연스럽게 분산)
- `#process` 섹션 이미지 2장이 원본에서 `data-alt`(검색엔진에 노출되지 않는 속성)로만 되어 있던 것을 실제 `alt` 속성으로 수정
- `title.png`는 og:image / twitter:image에만 사용, 본문·배너·사례 이미지에는 사용하지 않음 (기존과 동일하게 유지)

### 5. 구조화 데이터 (JSON-LD)
- **LocalBusiness (`Plumber` + `LocalBusiness` 복합 타입)**: 업체명, 전화번호(010-9164-6943), 대표자(`founder`: 박상현), 사업자등록번호(`taxID`: 349-33-01300), 서비스 지역(시흥시 및 11개 동), 가격대(40,000~200,000원, 실제 가격표 기준), 24시간 영업, 네이버 블로그 `sameAs` 포함
- **FAQPage**: 본문 FAQ와 동일한 5개 질문/답변
- **BreadcrumbList**: 홈 > 시흥 누수탐지
- 사업장 도로명 주소는 아직 전달받지 못해 `PLACEHOLDER_STREET_ADDRESS_나중에_입력`으로 남겨두었습니다 (임의 생성 금지 원칙 준수). 주소가 확정되면 `index.html`의 `LocalBusiness.address.streetAddress` 값만 교체하면 됩니다.

### 6. 과최적화 방지
- 키워드는 문장 속에 자연스럽게 1회씩만 녹여 배치했고, 쉼표 나열식 키워드 반복은 사용하지 않았습니다.
- 존재하지 않는 후기, 수상 이력, 인증, 정확하지 않은 주소는 작성하지 않았습니다.
- 숨김 텍스트나 사용자에게 보이지 않는 키워드 삽입은 없습니다.

## Cloudflare Pages 배포 설정

- Framework preset: **None**
- Build command: **exit 0**
- Build output directory: **.**
- Production branch: **main**

## 배포 후 확인할 URL

- `https://onecare-siheung.pages.dev/`
- `https://onecare-siheung.pages.dev/robots.txt`
- `https://onecare-siheung.pages.dev/sitemap.xml`
- `https://onecare-siheung.pages.dev/title.png`
- `https://onecare-siheung.pages.dev/404` (존재하지 않는 경로로 접속해서 404.html이 뜨는지 확인)

## 배포 전 실제 값으로 교체해야 하는 Placeholder 목록

도메인(`onecare-siheung.pages.dev`), 대표자명(박상현), 사업자등록번호(349-33-01300), 네이버 서치어드바이저 소유확인 코드는 이미 실제 값으로 반영되었습니다.
남은 placeholder는 아래 2가지뿐입니다.

| Placeholder | 위치 | 설명 |
| --- | --- | --- |
| `GOOGLE_VERIFICATION_CODE_나중에_입력` | `google-site-verification` | Google Search Console 소유확인 코드 |
| `PLACEHOLDER_STREET_ADDRESS_나중에_입력` | JSON-LD `LocalBusiness.address.streetAddress` | 실제 사업장 도로명 주소 (전달받는 대로 교체) |

전화번호(010-9164-6943), 네이버 블로그(`https://blog.naver.com/weqweq00`), 네이버 소유확인 메타태그(`24cdab7c2d80b482a93d68022103ec41548f8a6e`)는 이미 실제 값이 반영되어 있습니다.

## 네이버 서치어드바이저 등록 순서

`naver-site-verification` 메타태그는 이미 실제 코드로 반영되어 있으므로, Cloudflare Pages에 배포한 뒤 아래 순서로 바로 진행하면 됩니다.

1. [네이버 서치어드바이저](https://searchadvisor.naver.com)에서 사이트 등록: `https://onecare-siheung.pages.dev/`
2. 소유확인 진행 — "HTML 태그" 방식 선택 (이미 `index.html`에 코드가 들어가 있으므로 바로 확인 버튼 클릭)
3. Cloudflare Pages 배포 완료 확인 (`https://onecare-siheung.pages.dev/` 정상 접속, GitHub push 후 자동 재배포되었는지 확인)
4. 서치어드바이저에서 소유확인 완료 클릭
5. URL 검사 — 페이지 접속, robots.txt/sitemap.xml 접근, 로봇 메타 `index,follow`, 제목/설명/OG/canonical/모바일 접근성 정상 노출 확인
6. 웹 페이지 수집 요청
7. 사이트맵 제출: `https://onecare-siheung.pages.dev/sitemap.xml`
8. 며칠 뒤 네이버 검색창에서 `site:onecare-siheung.pages.dev`로 색인 확인, 이후 `시흥 누수탐지` 키워드로 순위 확인

## 최종 목표 재확인

이번 SEO 작업의 최우선 목표는 네이버에서 `시흥 누수탐지` 검색 시 상위 노출입니다.
다만 검색 순위는 네이버 알고리즘, 도메인 신뢰도, 경쟁 사이트, 클릭률, 네이버 플레이스/블로그 노출 등 다양한 요인에 따라 달라지며, 이 작업만으로 1위를 보장하지는 않습니다.
정식 오픈 후에는 실제 후기 확보, 네이버 블로그·플레이스 연동, 페이지 로딩 속도(이미지 압축) 개선을 함께 진행하는 것을 권장합니다.

## 참고 사항

- `images/` 폴더의 원본 사진(카카오톡 전송 사진)은 파일 용량이 장당 약 3~5MB로 다소 큰 편입니다. 정식 오픈 전에는 웹용으로 압축(예: 1~2MB 이하, 1600px 폭 내외)하는 것을 권장하나, 이번 작업에서도 원본 파일명/내용은 임의로 변경하지 않았습니다.
- 원본 이미지 폴더(`Image/`)와 `screen.png`는 참고용으로 프로젝트에 남겨두었으며, Cloudflare Pages 배포 결과물에는 영향을 주지 않습니다. 필요 없으면 직접 삭제하셔도 됩니다.
