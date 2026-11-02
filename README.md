# 👑 몽유록 (Mongyurok)

> 조선 왕과 대화하며 역사를 배우는 캐릭터형 AI 챗봇

---

## 📑 목차
1. [주요 역할](#-주요-역할)
2. [기술 스택](#기술-스택)
3. [개요](#-개요)
4. [시스템 구성도](#-시스템-구성도)
5. [ERD](#-erd)
6. [산출물](#-산출물)
7. [주요 기능](#-주요-기능)
---

## 👥 주요 역할
### 🐸 류지우(외 4명)
- 프론트엔드 및 백엔드
- UI/UX 설계
- 조선왕조실록 데이터 전처리 및 ChromaDB 적재
---

<a id="기술-스택"></a>
## 🛠️ 기술 스택

| 구분 | 기술 |
|---|---|
| 💻 Backend | Django |
|  | FastAPI |
| 🤖 AI / LLM | EXAONE-3.5-2.4B-Instruct (독대 모드) |
|  | OpenAI API (GPT, 역할극 모드) |
|  | LangChain |
|  | LangGraph |
| 📚 Retrieval | ChromaDB |
|  | HuggingFace Embedding (KURE-v1) |
| 🗄️ Database | MySQL (RDS) |
| ☁️ Infra | AWS EC2 |
|  | RunPod |
|  | Nginx |
|  | Gunicorn |
| 🐳 DevOps | Docker |
---
## 🔍 개요

### 📚 프로젝트 배경  
  
<p align="left">
<img width="500" height="500" alt="image" src="https://github.com/user-attachments/assets/03bb7129-01b8-41bc-8ce6-3f04fa8ede8f" /><br>
  https://www.mk.co.kr/news/it/11983531  
</p>
<p align="left">
최근 AI 챗봇 시장에서는 캐릭터와 대화하는 서비스가 높은 이용률과 사용 시간을 기록하고 있다.<br>
이는 챗봇이 정보 검색 도구를 넘어 감정적 교감과 몰입형 경험을 주는 서비스로 확장되고 있음을 보여준다.
</p> 
<p align="left">
  <img width="500" height="500" alt="image" src="https://github.com/user-attachments/assets/970130ec-a0fd-4372-b653-98e54ddf2eb1" /><br>
  https://n.news.naver.com/article/006/0000135557?sid=103 
</p>   
<p align="left">
또한 역사 드라마와 콘텐츠의 흥행으로 조선 시대와 역사 인물에 대한 관심이 검색과 탐색으로 이어지고 있다.<br>
이는 역사적 배경과 인물을 더 깊이 알고자 하는 사용자 니즈가 있음을 보여준다.
</p>   
  
<p align="left">
  <img src="https://github.com/user-attachments/assets/c998bd6d-a7e7-4708-bc78-5be3b9754642" width="500"/>
  <img src="https://github.com/user-attachments/assets/8e1d0e51-27fd-429f-a5f8-642623c98f69" width="500"/>
</p>  
<p align="left">
실제로 제타, 크랙 등의 캐릭터 기반 챗봇 플랫폼에서는 조선, 왕, 동양풍 등을 소재로 한 캐릭터가 다수 등장하고 있으며<br>
사용자들 또한 해당 주제를 기반으로 한 대화형 콘텐츠를 적극적으로 소비하고 있다.  
</p>   
  
<p align="left">
  <img src="https://github.com/user-attachments/assets/75ffdb25-ab5f-4beb-bfba-248d19f8d47f" width="500"/>
  <img src="https://github.com/user-attachments/assets/b6d1f37a-7614-4cee-a148-2760f35b0d53" width="500"/>
  https://contents.history.go.kr/front/hm/view.do?levelId=hm_074_0050 
</p>  
<p align="left">
그러나 기존 역사 캐릭터 챗봇은 인물의 말투나 분위기를 자연스럽게 구현하는 데 강점이 있지만 역사적 사실에 대한 답변에 어려움이 있다.<br>
예시 대화에서도 캐릭터는 자연스럽게 답하지만 실제 사료와 비교했을 때 역사적 오류가 포함될 수 있음을 확인할 수 있다.<br><br>
오른쪽 자료는 질문한 내용에 대해 국사편찬위원회에서 제공하고 있는 역사 원문 및 해설로 객관적 사료를 기반으로 해당 정보가 실제 역사적 사실과 다름을 보여준다.
이는 현재 캐릭터 챗봇이 몰입감 있는 대화 경험은 제공할 수 있으나 정보의 정확성과 신뢰성 측면에서는 검증되지 않은 내용을 생성할 가능성이 있다는 문제를 보여준다.
</p>  
<p align="left">
따라서 본 프로젝트는 이러한 시장 흐름과 사용자 니즈를 반영하여, 조선시대 인물을 기반으로 하되 단순한 캐릭터 재현을 넘어 역사적 사실과 인물의 성격을 함께 반영한 몰입형 역사 캐릭터 챗봇 서비스를 구현하고자 한다.
</p>  

### 🎯 프로젝트 목표  
- 조선시대 인물의 성격과 말투를 반영한 자연스러운 대화 구현  
- 역사적 사실 기반의 정확한 정보 제공 (RAG 기반)  
- 사용자 맞춤형 역할/상황 설정을 통한 몰입형 경험 제공  
  
---

## 🧩 시스템 구성도

<img width="1260" height="530" alt="Frame" src="https://github.com/user-attachments/assets/c7ac6d71-e1a3-4804-a7a5-fdbdc1a94ec0" />

---
## 📋 ERD

<img width="1132" height="777" alt="image" src="https://github.com/user-attachments/assets/b148e32f-5bfd-4de1-9df9-e61f22a6505f" />

---

## 📃 산출물
  
- [요구사항 정의서](docs/req_1.pdf)  
  
- [화면설계서](docs/scr_design.pdf)  

---

## 📌 주요 기능

### 메인 화면 (독대 모드)
<p align="center">
  <img src="https://github.com/user-attachments/assets/fa359559-7b02-4840-986e-1343e0d1831b" width="700"/>
  <br/>
</p>

---

### 독대 모드 캐릭터 상세보기
<p align="center">
  <img src="https://github.com/user-attachments/assets/59269281-4401-4a42-bd4f-b5f2cf3ef429" width="700"/>
</p>

---

### 역할극 모드 화면
<p align="center">
  <img src="https://github.com/user-attachments/assets/4aa12659-ce83-4748-8539-e06ae4f4a8c2" width="700"/>
  <br/>
</p>

---

### 역할극 모드 상세보기
<p align="center">
  <img src="https://github.com/user-attachments/assets/8a2c53e0-0f35-4c2a-847a-542ee2668081" width="700"/>
</p>

---

### 로그인
<p align="center">
  <img src="https://github.com/user-attachments/assets/02154ace-54f1-4554-9950-327a206c002c" width="700"/>
</p>

---

### 🧾 회원가입

#### 약관 동의
<p align="center">
  <img src="https://github.com/user-attachments/assets/d962bfe7-fbb7-4b9b-b170-2a95b9bfe42f" width="700"/>
  <br/>
  <img src="https://github.com/user-attachments/assets/13f8a139-d83e-4760-b343-12d4a7c0fffc" width="700"/>
</p>

---

#### 이용 약관
<p align="center">
  <img src="https://github.com/user-attachments/assets/0442d305-888e-4649-8655-8a5d8b5ba180" width="700"/>
</p>

---

#### 개인정보 수집 및 이용 동의
<p align="center">
  <img src="https://github.com/user-attachments/assets/2b6232f9-73c4-489c-9945-c062ab8b1087" width="700"/>
</p>

---

#### 회원가입
<p align="center">
  <img src="https://github.com/user-attachments/assets/d350567a-9753-46a3-b0aa-7ba098fea65c" width="700"/>
</p>

---

### 독대 모드 페르소나 설정
<p align="center">
  <img src="https://github.com/user-attachments/assets/3fb1fd88-3a6e-439e-b52d-d461947d11a5" width="400"/>
</p>

---

### 역할극 모드 페르소나 설정
<p align="center">
  <img src="https://github.com/user-attachments/assets/1a7411d1-5aee-4840-ae59-8a256ff92292" width="400"/>
</p>

---

### 독대 모드 실시간 채팅
<p align="center">
  <img src="https://github.com/user-attachments/assets/70d6c6d4-c77c-4752-8300-e5b101d9f1c8" width="400"/>
  <br>
  <img src="https://github.com/user-attachments/assets/6773d00f-008f-4387-9aa0-d32b8bbf573e" width="400"/>
</p>

---

### 역할극 모드 실시간 채팅
<p align="center">
  <img src="https://github.com/user-attachments/assets/c7366357-4ca7-4743-a806-98e87634c63e" width="400"/>
  <br>
  <img src="https://github.com/user-attachments/assets/77f97cc1-c3ee-47ee-b0fc-18b90c89ede9" width="400"/>
  <br>
  <img src="https://github.com/user-attachments/assets/fd56054e-704a-4ab8-98ac-faecd817a640" width="400"/>
</p>
