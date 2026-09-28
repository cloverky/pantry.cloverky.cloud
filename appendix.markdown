---
layout: page
title: 부록
permalink: /appendix/
---

<h2 id="terms" class="doc-h2">용어 정의</h2>
<div class="doc-table-wrap">
<table class="doc-table">
  <thead><tr><th>용어</th><th>정의</th></tr></thead>
  <tbody>
    <tr><td>재고 (Inventory)</td><td>사용자가 보유한 식재료 한 항목</td></tr>
    <tr><td>보관 위치 (storage)</td><td>냉장 · 냉동 · 실온</td></tr>
    <tr><td>재고 상태 (status)</td><td>정상 · 임박 · 만료 · 부족을 나타내는 뱃지</td></tr>
    <tr><td>추정 유통기한</td><td>유통기한이 없을 때 구매일 + 보관 기간(<code>shelfLifeDays</code>)으로 계산한 기한</td></tr>
    <tr><td>최소 수량 (minQuantity)</td><td>이 값 아래로 내려가면 부족으로 판단</td></tr>
    <tr><td>카탈로그</td><td>공개 식재료 기초 데이터 (Category · Food)</td></tr>
    <tr><td>영수증 스캔 (scan-key)</td><td>S3 키로 이미지를 읽어 OCR하고 품목을 뽑는 흐름</td></tr>
    <tr><td>사전가입</td><td>소셜 로그인 전에 회원가입을 마쳐야 하는 규칙</td></tr>
    <tr><td>취향 카드</td><td>레시피 평가(<code>recipe_feedback</code>)로 쌓는 개인 선호</td></tr>
    <tr><td>바운디드 컨텍스트 / 스포크</td><td>백엔드의 기능 단위 앱 (fridge, weather, auth 등)</td></tr>
  </tbody>
</table>
</div>
