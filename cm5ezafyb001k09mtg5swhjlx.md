---
title: "Webhook으로 Github와 Discord 연동"
seoTitle: "GitHub-Discord Webhook Integration Guide"
seoDescription: "연결된 Webhook을 통해 GitHub와 Discord를 연동하여 실시간으로 알림을 받고 협업 효율성을 높이는 방법을 알아보세요"
datePublished: Thu Jan 02 2025 07:02:02 GMT+0000 (Coordinated Universal Time)
cuid: cm5ezafyb001k09mtg5swhjlx
slug: webhook-github-discord
cover: https://cdn.hashnode.com/res/hashnode/image/upload/v1735800736392/c44b050d-b00e-4d98-8057-31c59b1f3375.webp
tags: github, webhooks, discord

---

현재 사이드 프로젝트에서 선택한 협업 도구는 Discord와 Github입니다. 소통 도구로 Slack을 많이 사용하지만 Slack 무료 버전은 메시지가 90일까지만 보존되는 단점이 있어 Discord 채택을 하게 됐습니다.

Github에서 발생하는 이슈 등록, PR 생성 및 기타 활동을 Discord 채널로 자동 알림을 받고자 합니다. 특히 온라인으로 진행되는 사이드 프로젝트에서는 소통과 협업의 중요성이 크며, Webhook을 활용한 Discord와 GitHub의 통합은 실시간 알림을 통해 개발자 협업의 큰 편리함을 제공합니다.

## ❓ Webhook 이란 뭘까요

Wikipedia는 Webhook을 다음과 같이 정의했습니다.

> A **webhook** is a method of augmenting or altering the behavior of a [web page](https://en.wikipedia.org/wiki/Web_page) or [web application](https://en.wikipedia.org/wiki/Web_application) with custom [callbacks](https://en.wikipedia.org/wiki/Callback_\(computer_programming\)). (Wikipedia)
> 
> “웹페이지 또는 웹앱에서 발생하는 특정 행동들을 커스텀 Callback으로 변환해주는 방법이다.”

쉽게 풀이하면, 웹에서 발생하는 **특정 행동(이벤트)을 감지하여 사용자가 원하는 작업을 자동으로 실행해주는 기술**을 뜻합니다.

Webhook은 **이벤트 발생 → 이벤트 정보 전송 → 원하는 작업 실행**이라는 단순한 흐름으로 작동합니다. 이와 같은 동작이 가능하기 위해서는 두 개의 주요 개체가 필요합니다

: **Webhook Provider와 Webhook Consumer**

* Webhook Provider는 이벤트 발생에 따른 이벤트 정보를 전송하는 앱/웹을 의미합니다.
    
* Webhook Consumer는 Provider에 제공한 이벤트 정보를 받아 처리하는 앱/웹을 의미합니다.
    

현재 문서에서는 **Github가 Webhook Provider, Discord가 Webhook Consumer**로 되겠네요!

Webhook의 응용성은 정말 다양합니다. 카드 결제가 완료되면 영수증을 이메일로 발송, 블로그 게시물이 작성되면 Twitter나 Facebook에 자동으로 게시 등등이 있습니다. Webhook 덕분에 다양한 분야에서 실시간 데이터 처리와 작업 자동화를 가능하게 해주어 생산성과 효율성을 크게 높입니다.

Webhook의 간단한 소개를 끝으로 본격적인 Github와 Discord 연동 해보시죠.

## 🔏 GitHub와 Discord를 Webhook으로 연동하는 방법

### 1\. Discord에서 Webhook 설정

(1) Discord에서 알림을 받을 채널로 이동 후 ⚙️(설정)을 눌러 채널 설정 페이지로 이동합니다.

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1735797322988/fcef6748-15d1-4c74-bcb4-e4bbad9ed9e8.png align="center")

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1735783183186/8cdc6437-3ee6-4b35-a900-f7243881a448.png align="center")

(2) 채널 설정 &gt; 연동 &gt; 웹후크 만들기 &gt; 새 웹후크를 클릭합니다.

( 웹훅이 존재하지 않는다면 웹후크 만들기 클릭 시, 자동으로 생성됩니다! )

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1735797352031/e70d0387-2358-4814-83dc-6af9132dd6ce.png align="center")

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1735797363838/e2525395-a3d9-462d-89ef-97823a68a723.png align="center")

(3) Webhook 이름과 아바타를 설정한 후, **Webhook URL**을 복사합니다.

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1735797379209/f2d8dd30-d9dc-4f24-83b6-a6d1fbe853fe.png align="center")

(4) **Webhook URL**을 복사 한 채로, 변경사항은 저장합니다.

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1735797400500/f0c0db80-7fec-49eb-8b3b-78e03af4d98c.png align="center")

### 2\. GitHub에서 Webhook 설정

(1) GitHub에서 연동하려는 Repository로 이동합니다.

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1735797439281/6144ec4a-1dfd-4b60-adc1-f04bf9719992.png align="center")

(2) 해당 Repository에 **Settings** &gt; **"Webhooks"** &gt; "**Add webhook"**을 클릭합니다.

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1735797448249/bedf03ed-fb08-4b57-8a79-9811061f76c8.png align="center")

(3) Discord에서 복사한 **Webhook URL**을 입력합니다. 반드시 주소 끝에 **꼭 /github를 넣어 주세요!**

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1735797478399/74a71f10-3b52-4234-be1e-454a06cd4591.png align="center")

(4) **Payload type**을 ***application/json***으로 설정합니다.

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1735797463010/cf229843-b3d8-4621-841b-360277ab090e.png align="center")

(5) 하위 목록에서는 GitHub에서 어떤 이벤트를 Discord로 보낼지 선택합니다.

* ![](https://cdn.hashnode.com/res/hashnode/image/upload/v1735797521435/9c72d6db-0d7e-4bf4-bd0f-a658a6aceecf.png align="center")
    
    SSL vertification 은 Enable SSL verificaition으로 체크합니다. ( HTTPS 보안을 강화합니다! )
    
* **Which events would you like to trigger this webhook?**
    
    * Just the push event : 리포지토리에서 코드를 푸시할 때만 Webhook이 동작합니다.
        
    * Send me everything : 리포지토리에서 발생하는 모든 이벤트를 Webhook으로 전송합니다.
        
    * Let me select individual events : 사용자가 Webhook으로 받을 이벤트를 개별적으로 선택할 수 있도록 설정합니다.
        

<details>
  <summary>Let me select individual events 목록 보기</summary>       
  <details>
    <summary>Branch 및 Tag 관련</summary>
    <strong>Branch or tag creation</strong>: 브랜치 또는 태그 생성 시 전송 <br />
    <strong>Branch or tag deletion</strong>: 브랜치 또는 태그 삭제 시 전송 <br />
    <strong>Branch protection configurations</strong>: 브랜치 보호 설정 활성화/비활성화 시 전송 <br />
    <strong>Branch protection rules</strong>: 브랜치 보호 규칙 생성, 삭제, 수정 시 전송
  </details>
  <details>
    <summary>Bypass 요청</summary>
    <strong>Push rulesets</strong>: 푸시 규칙 우회 요청 생성, 취소, 완료, 응답 수신, 응답 해제 시 전송 <br />
    <strong>Secret scanning push protections</strong>: 비밀 스캔 보호 우회 요청 생성, 취소, 완료, 응답 수신, 응답 해제. *(베타)*
  </details>
  <details>
    <summary>Check 관련</summary>
    <strong>Check runs</strong>: 체크 실행 생성, 요청, 재요청, 완료 시 전송 <br />
    <strong>Check suites</strong>: 체크 수트 요청, 재요청, 완료 시 전송
  </details>
  <details>
    <summary>Code 및 Commit 관련</summary>
    <strong>Code scanning alerts</strong>: 코드 스캔 경고 생성, 브랜치에서 수정, 닫힘 시 전송 <br />
    <strong>Commit comments</strong>: 커밋/차이에 댓글 추가 시 전송
  </details>
  <details>
    <summary>Collaborator 관련</summary>
    <strong>Collaborator add/remove/changed</strong>: 협업자 추가, 제거, 권한 변경 시 전송
  </details>
  <details>
    <summary>Custom Properties</summary>
    <strong>Custom property values</strong>: 리포지토리 사용자 정의 속성 값 변경 시 전송
  </details>
  <details>
    <summary>Dependabot 관련</summary>
    <strong>Dependabot alerts</strong>: 경고 생성, 수정, 해제, 재도입 시 전송
  </details>
  <details>
    <summary>Deploy 관련</summary>
    <strong>Deploy keys</strong>: 배포 키 생성, 삭제 시 전송 <br />
    <strong>Deployment statuses</strong>: 배포 상태 업데이트(API) 시 전송 <br />
    <strong>Deployments</strong>: 배포 생성, 삭제 시 전송
  </details>
  <details>
    <summary>Discussion 및 댓글 관련</summary>
    <strong>Discussions</strong>: 토론 생성, 수정, 닫힘, 답변됨, 라벨 변경 등 시 전송 <br />
    <strong>Discussion comments</strong>: 토론 댓글 생성, 수정, 삭제 시 전송
  </details>
  <details>
    <summary>Fork</summary>
    <strong>Forks</strong>: 리포지토리 포크 시 전송
  </details>
  <details>
    <summary>Issue 관련</summary>
    <strong>Issues</strong>: 이슈 생성, 수정, 삭제, 상태 변경 등 시 전송 <br />
    <strong>Issue comments</strong>: 이슈 댓글 생성, 수정, 삭제 시 전송
  </details>
  <details>
    <summary>Labels</summary>
    <strong>Labels</strong>: 라벨 생성, 수정, 삭제 시 전송
  </details>
  <details>
    <summary>Merge 관련</summary>
    <strong>Merge groups</strong>: 병합 그룹 체크 요청, 삭제 시 전송
  </details>
  <details>
    <summary>Milestones</summary>
    <strong>Milestones</strong>: 마일스톤 생성, 수정, 삭제, 상태 변경 시 전송
  </details>
  <details>
    <summary>Packages</summary>
    <strong>Packages</strong>: 패키지 게시, 업데이트 시 전송
  </details>
  <details>
    <summary>Page 및 Wiki</summary>
    <strong>Page builds</strong>: 페이지 빌드 완료 시 전송 <br />
    <strong>Wiki</strong>: Wiki 페이지 업데이트 시 전송
  </details>
  <details>
    <summary>Pull Request 관련</summary>
    <strong>Pull requests</strong>: PR 생성, 수정, 상태 변경 등 시 전송 <br />
    <strong>Pull request reviews</strong>: PR 리뷰 제출, 수정, 해제 시 전송 <br />
    <strong>Pull request review comments</strong>: PR 차이 댓글 생성, 수정, 삭제 시 전송 <br />
    <strong>Pull request review threads</strong>: PR 리뷰 스레드 해결, 미해결 시 전송
  </details>
  <details>
    <summary>Push</summary>
    <strong>Pushes</strong>: 리포지토리에 Git 푸시 발생 시 전송
  </details>
  <details>
    <summary>Releases</summary>
    <strong>Releases</strong>: 릴리스 생성, 수정, 게시, 삭제 시 전송
  </details>
  <details>
    <summary>Repository 관련</summary>
    <strong>Repositories</strong>: 리포지토리 생성, 삭제, 상태 변경, 이름 변경 등 시 전송 <br />
    <strong>Repository advisories</strong>: 리포지토리 권고 생성, 보고 시 전송 <br />
    <strong>Repository imports</strong>: 리포지토리 가져오기 성공, 실패, 취소 시 전송 <br />
    <strong>Repository rulesets</strong>: 리포지토리 규칙 생성, 수정, 삭제 시 전송 <br />
    <strong>Repository vulnerability alerts</strong>: 취약성 경고 생성, 수정, 해제 시 전송
  </details>
  <details>
    <summary>Secret Scanning</summary>
    <strong>Secret scanning alerts</strong>: 비밀 스캔 경고 생성, 수정, 유출 시 전송 <br />
    <strong>Secret scanning scans</strong>: 비밀 스캔 완료 시 전송
  </details>
  <details>
    <summary>Security 관련</summary>
    <strong>Security and analyses</strong>: 코드 보안 기능 활성화/비활성화 시 전송
  </details>
  <details>
    <summary>Stars</summary>
    <strong>Stars</strong>: 리포지토리에 스타 추가, 삭제 시 전송
  </details>
  <details>
    <summary>Workflow 관련</summary>
    <strong>Workflow jobs</strong>: 워크플로 작업 대기열 추가, 진행 중, 완료 시 전송 <br />
    <strong>Workflow runs</strong>: 워크플로 실행 요청, 완료 시 전송
  </details>
</details>

> **Nettee Backend는 이슈와 PR을 확인하기 위해 다음 목록을 선택했습니다.**

* **Branch or tag creation**: 브랜치 또는 태그 생성 시 전송
    
* **Issues**: 이슈 생성, 수정, 삭제, 상태 변경 등 시 전송
    
* **Issue comments**: 이슈 댓글 생성, 수정, 삭제 시 전송
    
* **Merge groups**: 병합 그룹 체크 요청, 삭제 시 전송
    
* **Pull requests**: PR 생성, 수정, 상태 변경 등 시 전송
    
* **Pull request reviews**: PR 리뷰 제출, 수정, 해제 시 전송
    
* **Pull request review comments**: PR 차이 댓글 생성, 수정, 삭제 시 전송
    
* **Pull request review threads**: PR 리뷰 스레드 해결, 미해결 시 전송
    

(6) 선택이 완료되면 **Active 상태로 체크 후 Add webhook을 클릭합니다.**

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1735799016857/58515cdc-6be7-48c6-b90f-d30d7439c7ec.png align="center")

* Active 체크를 해제하신다면 **Webhook 비활성화 상태**로 변경 됩니다.
    

### 3\. Webhook 테스트 해보기

(1) 선택하신 이벤트를 실행합니다. 추가한 Webhook은 이슈 등록 이벤트를 설정했으므로 이슈를 생성합니다.

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1735799032159/3c5d6121-4df2-40bf-83de-602fba14f1d3.png align="center")

(2) Discord에 알림이 오는지 확인합니다!

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1735799062252/856977b0-1372-4d52-b184-d0e8d4857c92.png align="center")

이제 해당 레포지토리에 대해 실시간으로 알림을 받고 확인할 수 있게 되었습니다.👍🏻