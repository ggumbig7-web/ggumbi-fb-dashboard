# GGUMBI F&B 대시보드

GGUMBI F&B 사업팀용 매출·원가·손익 실시간 관리 대시보드입니다.

- **라이브 URL**: https://ggumbig7-web.github.io/ggumbi-fb-dashboard/
- **배포 방식**: GitHub Pages (저장소 루트 정적 호스팅, 빌드 시스템 없음)
- **구성**: 순수 정적 HTML + JS. index.html 하나로 동작하며 Chart.js 4.4.0과 chartjs-plugin-datalabels 2.2.0을 CDN에서 로드합니다.

## 대시보드 구성

- 월간·주간 목표 대비 실적 (변동비/고정비/공헌이익/영업이익)
- 거래처별 수량·매출·목표진척율·원가·이익률 표
- 품목별 수익성 (쿠팡 vs 쿠팡 외 채널 구분)
- 채널별 매출 추이, 주요 품목군 매출 비중 차트, 주차별 비교

## 데이터 연동

구글시트를 CSV로 export해서 fetch하는 방식(export?format=csv&gid=...)을 사용합니다.

| 상수 | 값 | 설명 |
| --- | --- | --- |
| MAIN_SHEET | 11k69kRVVp7f1C3CADD81ytG6weKpPRB1ON9FR-1_4eo | 메인 데이터 시트 |
| GID_JEONGLI | 147807231 | "정리" 탭 — 모든 월의 W열 원가단가 기준 |
| HIST_SHEET | 1qCA02HAl77VM-O7rGLMwpxkDFsj1uVpjEJEk4MTyOyQ | 이력(히스토리) 시트 |
| GID_HIST | 0 | 26년 쿠팡 채널 vs 쿠팡 외 비교 탭 |

이 상수들은 index.html 상단(약 304~308줄)에 정의되어 있습니다. 시트 구조나 GID가 바뀌면 이 값들을 함께 갱신해야 합니다.

## 설정값 저장/조회 API

설정값(목표치 등)은 별도 Google Apps Script 웹앱을 통해 저장/조회합니다.

- 엔드포인트: https://script.google.com/macros/s/AKfycbys5GCaFgXK09sEX3hikBDKwTkk07aKeb4G8umObLaPTtwCaCw6gX0-nJiGmhxEiXV3/exec
- 조회: ?action=getAll
- 저장: ?action=set&key=...&value=...

정의 위치: index.html:1064 부근.

## 참고

- 빌드 과정이 없으므로 index.html을 직접 수정하고 커밋하면 GitHub Pages에 그대로 반영됩니다.
- 이전 초안이었던 index_1.html은 사용처가 없어 정리했습니다(git 히스토리에서 복구 가능).
