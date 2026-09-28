---
layout: page
title: 프로젝트 소개
permalink: /about/
---

<h1 class="doc-h1">프로젝트 소개 — FridgeAI</h1>
<p class="doc-lead">냉장고 속 재료를 기억하고, 유통기한이 가까운 것부터 알려주며, 그 재료로 만들 요리를 추천한다</p>

<h2 class="doc-h2">핵심 소주제</h2>

<div class="doc-topics">

<div class="doc-topic">
  <p class="doc-topic-num">1</p>
  <div>
    <p class="doc-topic-title">유통기한 중심 재고 관리</p>
    <p class="doc-topic-body">식재료마다 수량, 유통기한, 보관 위치(냉장/냉동/실온), 최소 수량을 기록한다. 유통기한이 없으면 구매일과 보관 기간으로 추정하고(추정 표시), 임박·만료·부족 상태를 뱃지로 보여 준다.</p>
  </div>
</div>

<div class="doc-topic">
  <p class="doc-topic-num">2</p>
  <div>
    <p class="doc-topic-title">영수증 한 장으로 재고 채우기</p>
    <p class="doc-topic-body">영수증 사진을 S3에 올리면 Gemini Vision이 품목을 뽑는다. 사용자가 확인·수정한 품목만 재고에 담아 AI 인식 오류가 그대로 저장되지 않게 한다.</p>
  </div>
</div>

<div class="doc-topic">
  <p class="doc-topic-num">3</p>
  <div>
    <p class="doc-topic-title">지금 써야 하는 재료로 레시피 추천</p>
    <p class="doc-topic-body">임박 재료를 우선해 Gemini가 레시피를 추천하고, 평가(취향 카드)를 쌓아 개인화한다. 키가 없거나 호출이 실패해도 준비된 레시피로 대체해 화면이 비지 않는다. 비로그인 사용자에게는 시간대별 요리를 보여 준다.</p>
  </div>
</div>

<div class="doc-topic">
  <p class="doc-topic-num">4</p>
  <div>
    <p class="doc-topic-title">온프레미스 LLM 어시스턴트</p>
    <p class="doc-topic-body">대화형 어시스턴트는 로컬 GPU에서 vLLM으로 띄운 EXAONE을 쓴다. 웹은 채팅 요청만 통합 API(api.cloverky.cloud)로 프록시한다.</p>
  </div>
</div>

<div class="doc-topic">
  <p class="doc-topic-num">5</p>
  <div>
    <p class="doc-topic-title">웹 · 모바일 · 통합 백엔드</p>
    <p class="doc-topic-body">Next.js 웹(Vercel)과 Flutter 앱이 있고, 백엔드는 여러 프로젝트를 경로로 나눠 담은 헥사고날 구조의 FastAPI(Cloudflare 터널)다. FridgeAI는 <code>/api/fridge/*</code> 바운디드 컨텍스트를 쓴다.</p>
  </div>
</div>

</div>

<h2 class="doc-h2">주요 기능</h2>
<div class="doc-table-wrap">
<table class="doc-table">
  <thead><tr><th>기능</th><th>설명</th><th>상태</th></tr></thead>
  <tbody>
    <tr><td>재고 관리</td><td>식재료 CRUD, 소비·추가, 보관 위치·상태 관리</td><td><span class="doc-tag">구현</span></td></tr>
    <tr><td>영수증 스캔</td><td>S3 업로드 → Gemini Vision 추출 → 확인 후 재고 반영</td><td><span class="doc-tag">구현</span></td></tr>
    <tr><td>AI 레시피 추천</td><td>임박 재료 우선 추천, 폴백 레시피, 비로그인 시간대 추천</td><td><span class="doc-tag">구현</span></td></tr>
    <tr><td>취향 카드</td><td>레시피 평가(<code>recipe_feedback</code>)로 개인화</td><td><span class="doc-tag">구현</span></td></tr>
    <tr><td>AI 어시스턴트</td><td>EXAONE(vLLM) 채팅 프록시</td><td><span class="doc-tag">구현</span></td></tr>
    <tr><td>쇼핑 연결</td><td>부족 재료 감지 → 장바구니 메모 · 쇼핑몰 검색 링크</td><td><span class="doc-tag">구현</span></td></tr>
    <tr><td>위치 기반 날씨</td><td>좌표 → 한글 지명 + 날씨, 3단 폴백</td><td><span class="doc-tag">구현</span></td></tr>
    <tr><td>소셜 로그인</td><td>Google·Kakao·Naver, 사전가입 강제, 데모 계정, admin 역할</td><td><span class="doc-tag">구현</span></td></tr>
    <tr><td>냉장고 달리기</td><td>미니게임, 최고 기록 계정 저장</td><td><span class="doc-tag">구현</span></td></tr>
    <tr><td>스마트 알림</td><td>유통기한 D-3/D-1 · 재고 부족 푸시</td><td><span class="doc-tag muted">설계</span></td></tr>
    <tr><td>소비 패턴 분석</td><td>소비·폐기 통계</td><td><span class="doc-tag muted">설계</span></td></tr>
  </tbody>
</table>
</div>

<h2 class="doc-h2">기술 스택</h2>
<div class="doc-stack">
  <div class="doc-stack-item"><span class="doc-tag">WEB</span>Next.js 16 · React 19 · TypeScript · Tailwind v4 · shadcn/ui · Prisma 5</div>
  <div class="doc-stack-item"><span class="doc-tag">MOBILE</span>Flutter (Android · Web · Windows)</div>
  <div class="doc-stack-item"><span class="doc-tag">BACKEND</span>Python · FastAPI · SQLAlchemy 2 (async) · Alembic · Redis</div>
  <div class="doc-stack-item"><span class="doc-tag">AI</span>Gemini (Vision · 레시피) · EXAONE on vLLM · LangGraph</div>
  <div class="doc-stack-item"><span class="doc-tag">INFRA</span>Neon PostgreSQL · AWS S3 · Vercel · Cloudflare Tunnel · Docker Compose</div>
</div>

<h2 class="doc-h2">아키텍처</h2>
<div class="doc-table-wrap">
<table class="doc-table">
  <thead><tr><th>계층</th><th>기술</th><th>배포</th></tr></thead>
  <tbody>
    <tr><td>웹 (<code>lucky/</code>)</td><td>Next.js + Next API 라우트 + Prisma</td><td>Vercel · fridge.cloverky.cloud</td></tr>
    <tr><td>모바일 (<code>fortune/</code>)</td><td>Flutter</td><td>—</td></tr>
    <tr><td>API (<code>clover/</code>)</td><td>FastAPI, 헥사고날 · 바운디드 컨텍스트</td><td>Docker · Cloudflare Tunnel · api.cloverky.cloud</td></tr>
    <tr><td>DB</td><td>PostgreSQL</td><td>Neon</td></tr>
    <tr><td>파일</td><td>영수증 이미지</td><td>AWS S3</td></tr>
    <tr><td>LLM</td><td>EXAONE (vLLM, :8001)</td><td>로컬 WSL systemd</td></tr>
  </tbody>
</table>
</div>
