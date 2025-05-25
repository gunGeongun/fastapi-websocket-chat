# FastAPI 웹소켓 채팅 애플리케이션

이 프로젝트는 **FastAPI**를 기반으로 한 실시간 채팅 백엔드와 **React**로 구성된 프론트엔드로 구성된 채팅 애플리케이션입니다. 웹소켓을 통해 여러 채팅방에서 실시간 대화를 주고받을 수 있으며, **Docker** 환경에서 개발되었고 **ngrok**을 통해 외부 접속도 지원합니다.

## 🌐 데모 안내

로컬에서 실행하거나 ngrok을 통해 외부 접근 가능한 URL을 획득할 수 있습니다.

---

## 📁 프로젝트 구조

```
fastapi-websocket-chat/
├── backend/
│   ├── app/
│   │   └── app.py
│   ├── www/
│   │   └── static/
│   └── ngrok_setup.py
├── frontend/
│   ├── src/
│   │   ├── components/
│   │   ├── styles/
│   │   └── App.js
│   └── package.json
└── .gitignore
```

---

## 🚀 주요 기능

- 🔌 웹소켓 기반 실시간 채팅
- 🗂 4개의 고정 채팅방 제공 (일반, 기술, 취미, 음악/영화)
- 👥 입장/퇴장 알림
- 💬 방별 메시지 브로드캐스팅
- 🌍 ngrok으로 외부 접속 가능
- 📦 Docker 기반 개발 환경

---

## 🐳 Docker 컨테이너 설정

```bash
docker run -it --name chat-app -p 3000:3000 -p 22:22 ubuntu:20.04 /bin/bash
```

### 컨테이너 내부에서:
```bash
apt-get update && apt-get install -y \
  python3 python3-pip python3-venv nodejs npm git openssh-server sudo curl wget vim iproute2
```

---

## 🛠️ FastAPI 백엔드

1. `backend/` 디렉토리로 이동 후 가상환경 생성:
```bash
python3 -m venv venv
source venv/bin/activate
```

2. 필요한 패키지 설치:
```bash
pip install fastapi uvicorn websockets jinja2 python-multipart pyngrok
```

3. 서버 실행:
```bash
uvicorn app.app:app --host 0.0.0.0 --port 3000
```

---

## ⚛️ React 프론트엔드

1. 루트에서 React 앱 생성:
```bash
npx create-react-app frontend
cd frontend
```

2. 구조 설명:
- `RoomList`: 채팅방 목록 및 입장
- `ChatRoom`: 실시간 메시지 송수신
- 스타일: CSS 모듈

3. `package.json`에 프록시 설정:
```json
"proxy": "http://localhost:3000"
```

4. 빌드 및 정적 파일 복사:
```bash
npm run build
rm -rf ../backend/www/*
cp -r build/* ../backend/www/
```

---

## 🌐 ngrok을 통한 외부 접근

1. https://dashboard.ngrok.com/get-started/setup 에서 인증 토큰 획득
2. 설정 스크립트 실행:
```bash
cd backend
python ngrok_setup.py
```

---

## 🔐 GitHub 연동

1. 저장소 생성 후 커밋 및 푸시:
```bash
git add .
git commit -m "초기 커밋: FastAPI 웹소켓 채팅"
git push origin main
```

Personal Access Token을 비밀번호 대신 입력합니다.

---

## ✅ 향후 개선 과제

- [ ] 사용자 인증 기능 추가
- [ ] 데이터베이스 연동하여 채팅 로그 저장
- [ ] 개인 대화 (DM) 기능
- [ ] Docker Compose 구성

---

## 📝 라이선스

본 프로젝트는 [MIT 라이선스](LICENSE)를 따릅니다.

---

## 🙋‍♂️ 개발자 정보

작성자: 김건건
---

## 📸 스크린샷


