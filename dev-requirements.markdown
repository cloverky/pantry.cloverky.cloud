---
layout: page
title: 개발 요구 사항
permalink: /dev-requirements/
---

<h2 id="scope" class="doc-h2">1. 개발 범위</h2>
<div class="doc-table-wrap">
<table class="doc-table">
  <thead><tr><th>구분</th><th>범위</th></tr></thead>
  <tbody>
    <tr><td>웹</td><td>재고 · 영수증 · 레시피 · 어시스턴트 · 쇼핑 · 날씨 · 게임 · 로그인/회원가입</td></tr>
    <tr><td>모바일</td><td>인트로 영상, 랜딩, 공개 식재료 카탈로그, 위치 기반 날씨</td></tr>
    <tr><td>API</td><td><code>/api/fridge/*</code> (inventory · category · food · receipt · receipt-line · recipe-feedback · recipe-ingredients · game-scores · assistant · user), <code>/weather</code>, <code>/api/receipts/images</code>, <code>/auth/{provider}</code></td></tr>
    <tr><td>제외</td><td>영수증 원본의 DB 저장, 유통기한 푸시 알림, 소비 패턴 분석 (설계만)</td></tr>
  </tbody>
</table>
</div>

<h2 id="inventory" class="doc-h2">2. 재고 관리</h2>
<ul class="doc-body">
  <li>재고 항목은 이름, 수량, 단위, 유통기한, 구매일, 보관 위치(기본 냉장), 최소 수량, 상태(기본 정상)를 가진다.</li>
  <li>유통기한이 없으면 구매일 + 보관 기간(<code>shelfLifeDays</code>)으로 추정하고 <code>expiryIsEstimated</code>로 표시한다.</li>
  <li>수량이 최소 수량 아래로 내려가면 부족으로 보고 쇼핑 연결에 넘긴다.</li>
</ul>

<h2 id="receipt" class="doc-h2">3. 영수증 → 재고</h2>
<p class="doc-body">흐름: S3 업로드 → <code>/api/fridge/receipt/scan-key</code>(Gemini Vision) → 사용자 확인·수정 → <code>POST /api/fridge/inventory</code></p>
<ul class="doc-body">
  <li>OCR 엔진과 이미지 리더는 포트로 분리해 모델을 바꿔도 도메인 코드는 그대로 둔다.</li>
  <li>모델명은 하드코딩하지 않고 <code>GEMINI_MODEL</code> 환경변수로 받는다.</li>
  <li>인식 결과는 사용자가 확인한 것만 저장한다.</li>
</ul>

<h2 id="ai" class="doc-h2">4. AI 추천 · 어시스턴트</h2>
<ul class="doc-body">
  <li>레시피: Gemini 호출이 실패하거나 키가 없으면 준비된 레시피로 대체하고 실패 사실을 안내한다.</li>
  <li>어시스턴트: EXAONE(vLLM)으로 프록시하며, 웹은 채팅 요청만 통합 API로 보낸다.</li>
</ul>

<h2 id="auth" class="doc-h2">5. 인증 · 보안</h2>
<ul class="doc-body">
  <li>소셜 로그인은 사전가입한 사용자만 통과한다. provider까지 일치해야 하고, 미가입자는 회원가입 화면으로 보낸다.</li>
  <li>가입 의도는 Redis의 OAuth state에 담고, 연동 계정은 <code>user_oauth_accounts</code>에 저장한다.</li>
  <li>외부 API 키(OpenWeather, Gemini)는 서버에만 둔다.</li>
</ul>
