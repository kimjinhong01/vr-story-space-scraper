# VR 인터랙티브 스토리 게임

본 프로젝트는 Unity와 XR Interaction Toolkit을 기반으로 한 VR 인터랙티브 스토리 게임입니다.  
플레이어는 직접 상호작용하며 다양한 환경, 장치, 그리고 스토리 요소들을 경험하게 됩니다.

[![VR 인터랙티브 스토리 게임 시연 영상](https://img.youtube.com/vi/hvpG1fLjlkE/maxresdefault.jpg)](https://youtu.be/hvpG1fLjlkE)
[시연 영상 보기](https://youtu.be/hvpG1fLjlkE)

---

## 주요 기능

| 기능 | 설명 |
|------|------|
| 오디오 매니지먼트 | `AudioManager`를 통한 게임 내 모든 사운드 제어 |
| 버튼과 문 시스템 | 버튼을 눌러 애니메이션 + 사운드와 함께 문 열기 |
| 총기 시스템 | `MeteorPistol`: 레이캐스트 기반 타격 + 파괴 시스템 |
| 파괴 가능한 오브젝트 | 일정 시간 상호작용 후 파괴되고 파편으로 전환 |
| 조작 방식 설정 | Snap Turn / Continuous Turn 선택 가능 (`PlayerPrefs` 연동) |
| 씬 전환 | `FadeScreen`과 함께 자연스럽게 씬 변경 |
| 손 모델 처리 | 오브젝트를 잡을 때 손 모델을 감추고, 놓을 때 복원 |
| UI 사운드 | 버튼 클릭, 마우스 오버 사운드 효과 지원 |
| 소켓 제한 | 특정 태그 오브젝트만 장착 가능한 소켓 구현 |
| 쓰레기통 트리거 | 특정 태그 오브젝트가 진입 시 자동 제거 처리 |

---

## 폴더 구조 (일부)

```

Assets/
├── Scripts/
│   ├── Audio/
│   │   └── AudioManager.cs
│   ├── Interactions/
│   │   ├── ButtonPushOpenDoor.cs
│   │   ├── MeteorPistol.cs
│   │   ├── Breakable.cs
│   │   └── XRSocketTagInteractor.cs
│   ├── UI/
│   │   ├── GameStartMenu.cs
│   │   ├── SetOptionFromUI.cs
│   │   ├── UIAudio.cs
│   ├── System/
│   │   ├── SceneTransitionManager.cs
│   │   ├── FadeScreen.cs
│   │   └── PlaySteps.cs
│   ├── Environment/
│   │   ├── SpaceOutsideController.cs
│   │   ├── TrashCan.cs
│   │   └── TriggerZone.cs
│   └── Settings/
│       └── SetTurnTypeFromPlayerPref.cs

```

---

## 기술 스택

- Unity 2022+
- XR Interaction Toolkit
- Unity Timeline (PlayableDirector)
- C#
- VR 디바이스 지원 (Meta Quest, HTC Vive 등)

---

## 주요 구현 방식

### 씬 전환 시스템
- `SceneTransitionManager`를 통해 씬을 자연스럽게 페이드 효과와 함께 전환
- `FadeScreen`으로 알파값을 조절하여 시각적 몰입감을 높임

### 오디오 재생 방식
- `AudioManager`를 중심으로 전역 사운드 관리
- `PlayAudioFromAudioManager`, `UIAudio` 등을 통해 다양한 상황에 맞는 효과음 제공

### 상호작용 무기 시스템
- `MeteorPistol`은 XRGrabInteractable 기반으로 잡고 방아쇠를 당기면 발사
- 레이캐스트를 이용해 `Breakable` 오브젝트에 타격 가능

### 설정 저장 시스템
- `PlayerPrefs`를 활용해 회전 방식 설정 (Snap vs Continuous)을 저장/불러오기
- `SetOptionFromUI.cs`, `SetTurnTypeFromPlayerPref.cs`가 이를 처리

---

## 테스트 및 디버깅 팁

- VR 환경에서 작동 여부를 반드시 XR 디바이스로 테스트하세요
- `AudioManager`에 사운드 등록이 누락되지 않았는지 확인하세요
- `FadeScreen`이 제대로 작동하려면 Renderer가 있는 오브젝트가 필요합니다
- `TriggerZone`의 `targetTag` 설정 누락 시 이벤트가 발생하지 않습니다

---

## 기여 및 확장 아이디어

- 햅틱 피드백 추가: XR 디바이스 진동을 활용한 몰입감 향상
- 퍼즐 시스템 확장: `XRSocketTagInteractor`를 퍼즐 요소로 활용
- 저장/불러오기 시스템: PlayerPrefs 기반의 게임 진행 상태 저장
- 스토리 연출 강화: `PlaySteps`와 Timeline으로 컷씬 연출 다양화

---

## 제작자

- 기획/개발/설계: 김진홍
- 영상 시연: [YouTube 링크](https://youtu.be/hvpG1fLjlkE)
```
