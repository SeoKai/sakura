## 프로젝트 정보

웹 소켓을 활용할 수 있는 미니 프로젝트를 만들고 싶어 **실시간 코드 협업 툴** 이라는 대략적인 프로젝트 목표를 가지고 방향성을 설정하는 중이다.

이 프로젝트를 통해 WebSocket 기반의 실시간 통신 구조를 직접 설계하고, 프론트와 백엔드 간 메시지 흐름을 코드로 구현하는 경험을 목표로 한다.

---

### 최소 기능 제품 설계 (MVP)

1. **닉네임 기반 임시 로그인 (MVP)**
    - 사용자는 최초 접속 시 닉네임을 입력하고, 해당 정보를 `localStorage`에 저장하여 세션 간 유지
    - WebSocket 메시지 송수신 시 닉네임이 포함되어, 사용자 식별 가능
    - 별도의 회원가입 또는 인증 절차 없이 빠른 접속이 가능하도록 구성
2. **JWT 기반 로그인 (MVP 이후 확장)**
    - MVP 기능이 안정적으로 구축된 이후, Spring Security + JWT를 기반으로 한 로그인 시스템 도입 예정
    - 사용자 인증 및 권한 분리를 통해 협업 권한 관리 및 기능 제한(예: 읽기 전용 뷰어 등) 가능하게 확장할 계획
3. **세션 생성 및 참여**
    - 사용자가 새로운 협업 세션을 생성할 수 있으며, 세션 ID를 통해 타 사용자가 해당 세션에 참여할 수 있도록 한다.
    - 세션은 고유한 UUID 기반으로 식별된다.
    - 세션 간 메시지가 분리되도록 구현한다 (Room 구조).
4. **채팅 기능**
    - 동일 세션에 참여한 사용자끼리 실시간 텍스트 채팅이 가능하다.
    - WebSocket을 통해 메시지를 주고받으며, 메시지는 송신자 이름과 함께 표시된다.
