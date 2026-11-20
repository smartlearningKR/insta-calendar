# insta-calendar

@ebslistening_official 인스타그램 콘텐츠를 한눈에 보는 보기 전용 캘린더예요. GitHub Pages로 공개됩니다.

## 구조
- `index.html` — 캘린더 페이지. `data/weeks.json`을 읽어서 그립니다.
- `data/weeks.json` — 주차별 일정. **새 주는 배열 끝에 추가만 하고, 지난 주는 지우거나 고치지 않습니다**(기록 보존).

## 한 주 데이터 형식
```json
{
  "id": "2026-11-30",            // 그 주 월요일 날짜
  "label": "11/30~12/4",
  "note": "기말 대비",            // 짧은 시기 메모
  "doc": "https://claude.ai/artifact/...",  // 주간 제안서 링크(없으면 빈 문자열)
  "summary": "",                 // 지난주 성과 분석 요약 등 (선택, 줄바꿈 가능)
  "items": [
    {"date": "2026-11-30", "format": "피드", "area": "단어",
     "hook": "표지 후킹 문구", "insight": "인사이트 한 줄, [[형광 표시할 부분]]",
     "file": "릴스_1201_요약.mp4", "note": "게시 메모(선택)",
     "detail": {
       "insight": "인사이트 전체 문단", "sources": [{"title": "출처명", "url": "https://..."}],
       "why": "왜 먹히나", "lead": "장 수·톤 메모(선택)",
       "slides": [{"title": "", "body": "", "highlight": "", "last": ""}],   // 피드
       "scenes": [{"time": "0–2.6초", "big": "", "small": ""}],              // 릴스
       "caption": "캡션 전체", "memo": "참고 메모(선택)"
     }}
  ]
}
```
`detail`은 주간 제안서의 내용을 그대로 옮긴 것으로, 페이지 아래 '콘텐츠 상세'에 표시돼요.
`format`은 `피드` 또는 `릴스`. 기본 배치는 월 피드, 화 릴스, 수 피드, 목 릴스, 금 피드.
