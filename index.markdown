---
layout: cover
title: "FridgeAI : 유통기한 기반 식재료 관리 및 AI 레시피 추천 서비스"
title_l1: "FridgeAI : 유통기한 기반 식재료 관리 및"
title_l2: "AI 레시피 추천 서비스"
permalink: /
eyebrow: 개 발 제 안 서
subtitle_en: "FridgeAI: An Expiry-Aware Food Inventory and AI Recipe Recommendation Service"
project_name: "AI 기반 냉장고 식재료 관리 및 맞춤 레시피 추천 플랫폼"
system_name: "FridgeAI"
dev_period: "2026년 7월 7일 (화) ~ 진행 중"
dev_period_note: "첫 커밋 7.7 · 9.22 Vercel 이전"
dev_team_name: cloverky
dev_team_members: "박소연"
dev_team_count: "1인 개발"
github_url: "https://github.com/cloverky/cloverky.cloud"
doc_repo_url: "https://github.com/cloverky/pantry.cloverky.cloud"
doc_url: "https://pantry.cloverky.cloud"
demo_url: "https://fridge.cloverky.cloud"
demo_note: "Vercel 배포 · API api.cloverky.cloud"
---

## 주요 기능

| 기능 | 설명 |
|------|------|
| 재고 관리 | 수량·유통기한·보관 위치(냉장/냉동/실온) 관리, 임박 순 정렬 |
| 영수증 스캔 | S3 업로드 → Gemini Vision 품목 추출 → 확인 후 재고 반영 |
| AI 레시피 추천 | 지금 써야 하는 재료 기반 Gemini 추천, 실패 시 준비된 레시피로 대체 |
| AI 어시스턴트 | 온프레미스 EXAONE(vLLM) 기반 냉장고 대화 |
| 위치 기반 날씨 | OpenWeather → Open-Meteo → 서울 순 폴백 |
| 소셜 로그인 | Google·Kakao·Naver, 사전가입 강제 |
| Flutter 앱 | 인트로 영상 · 공개 식재료 카탈로그 · 날씨 |
