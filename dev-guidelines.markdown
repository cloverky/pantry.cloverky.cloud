---
layout: page
title: 주요 개발 수행 지침
permalink: /dev-guidelines/
---

<h2 id="architecture" class="doc-h2">1. 아키텍처 원칙</h2>
<ul class="doc-body">
  <li>백엔드는 DDD + 헥사고날 구조다. 기능은 <code>clover/apps/{fridge, auth, weather, ...}</code> 바운디드 컨텍스트(스포크)로 나눈다.</li>
  <li>스포크끼리 직접 import하지 않는다. 외부 연동(OCR, 이미지 저장소, 날씨)은 포트/어댑터로 감싼다.</li>
  <li>외부 API는 실패를 전제로 설계한다. 날씨는 OpenWeather → Open-Meteo → 서울, 레시피는 Gemini → 준비된 레시피 순으로 폴백한다.</li>
</ul>

<h2 id="harness" class="doc-h2">2. 하네스 — 코드 작성 후 필수 실행</h2>
<p class="doc-body">린터 에러는 무시하지 않는다. 수정한 뒤에 완료로 본다.</p>
<div class="doc-table-wrap">
<table class="doc-table">
  <thead><tr><th>영역</th><th>명령</th></tr></thead>
  <tbody>
    <tr><td>Flutter (<code>fortune/</code>)</td><td><code>flutter analyze --fatal-infos</code> · <code>dart format --set-exit-if-changed .</code></td></tr>
    <tr><td>Python (<code>clover/</code>)</td><td><code>ruff check . --fix</code> · <code>ruff format .</code> · <code>mypy .</code></td></tr>
    <tr><td>Next.js (<code>lucky/</code>)</td><td><code>npm run lint</code> · <code>npx prettier --write .</code></td></tr>
  </tbody>
</table>
</div>

<h2 id="docs" class="doc-h2">3. 설계 문서</h2>
<p class="doc-body">기능마다 설계(design)와 구현 계획(plan)을 먼저 쓰고 구현한다. 저장소 <code>_docs/</code>에 있다.</p>
<div class="doc-table-wrap">
<table class="doc-table">
  <thead><tr><th>기능</th><th>핵심 결정</th><th>작성</th></tr></thead>
  <tbody>
    <tr><td>식재료 카탈로그 둘러보기</td><td>앱 <code>시작하기</code>가 동작하지 않던 문제 → 인증 없는 공개 카탈로그, 멱등 시드 스크립트</td><td>8.2</td></tr>
    <tr><td>위치 기반 날씨</td><td>위젯 탭 시 위치 권한 요청, 한글 지명, <code>/weather</code>는 항상 200, lat/lon 한쪽만 오면 422</td><td>8.1</td></tr>
    <tr><td>영수증 → 재고</td><td>OCR·이미지 리더 포트 분리, 사용자 확인 후 저장, DB 저장·알림은 범위 밖</td><td>8.4</td></tr>
    <tr><td>소셜 로그인 사전가입</td><td>"로그인이 곧 가입"을 막음, provider 일치 필수, 우회 라우터 제거</td><td>8.2</td></tr>
  </tbody>
</table>
</div>
