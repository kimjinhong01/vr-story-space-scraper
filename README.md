# Unity VR 인터랙티브 스토리 게임

![Story Preview](https://img.youtube.com/vi/hvpG1fLjlkE/maxresdefault.jpg)

[**시연 영상 보기**](https://youtu.be/hvpG1fLjlkE)

---

## 프로젝트 개요

Unity와 XR Interaction Toolkit을 기반으로 개발된 **VR 인터랙티브 스토리 게임**입니다.
플레이어는 다양한 오브젝트와 환경 요소와 직접 상호작용하면서 몰입감 있는 스토리를 경험하게 됩니다.
스토리텔링, 애니메이션, 인터랙션을 **VR 환경에 자연스럽게 녹여낸** 것이 특징입니다.

---

## 주요 기능

| 시스템       | 설명                                                         |
| --------- | ---------------------------------------------------------- |
| 오디오 관리    | `AudioManager`를 통한 전체 사운드 제어 (BGM, SFX, UI 등)              |
| 스토리 연출    | Unity Timeline 기반 연출 시스템 (`PlayableDirector`, `PlaySteps`) |
| 무기 시스템    | `MeteorPistol`을 통한 상호작용/파괴형 오브젝트 타격                        |
| 파괴 시스템    | 일정 시간 상호작용 시 `Breakable` 오브젝트가 파괴 및 파편화                    |
| UI 시스템    | 버튼 클릭, 마우스 오버 사운드, 씬 전환 등 자연스러운 인터페이스                      |
| 조작 설정     | Snap Turn / Continuous Turn 선택 가능 (`PlayerPrefs` 저장)       |
| 제한 소켓 시스템 | 특정 태그만 장착 가능한 XR 소켓 구현                                     |
| 환경 인터랙션   | 문 열기, 트리거 진입, 쓰레기통 제거 등 환경과의 상호작용 가능                       |

---

## 게임 흐름 예시

```
Start → Scene 연출 (PlaySteps)
→ 오브젝트 탐색 / 버튼 상호작용
→ 문 열기 / 이동 → 다음 씬 전환
→ 특정 태그 오브젝트 처리 → 엔딩/클리어

※ 스토리 연출은 Timeline + 인터랙션으로 구성
```

---

## 코드 및 폴더 구조

```bash
Assets/
├── Scripts/
│   ├── Audio/
│   │   └── AudioManager.cs            # 전역 사운드 관리
│   ├── Interactions/
│   │   ├── MeteorPistol.cs           # 무기 발사 및 타격
│   │   ├── Breakable.cs              # 파괴 가능한 오브젝트
│   │   ├── ButtonPushOpenDoor.cs     # 버튼 클릭 → 문 열기
│   │   └── XRSocketTagInteractor.cs  # 특정 태그만 장착 가능한 소켓
│   ├── UI/
│   │   ├── UIAudio.cs                # UI 사운드 처리
│   │   ├── GameStartMenu.cs
│   │   └── SetOptionFromUI.cs
│   ├── System/
│   │   ├── SceneTransitionManager.cs # 씬 전환 관리
│   │   ├── FadeScreen.cs             # 페이드 인/아웃 연출
│   │   └── PlaySteps.cs              # Timeline 실행 및 연출 스텝
│   ├── Environment/
│   │   ├── TrashCan.cs               # 쓰레기 오브젝트 처리
│   │   └── TriggerZone.cs            # 특정 태그 진입 감지
│   └── Settings/
│       └── SetTurnTypeFromPlayerPref.cs
```

---

## 조작 방법 (VR 컨트롤러 기준)

| 기능       | 조작 방식                                  |
| -------- | -------------------------------------- |
| 이동       | Snap Turn / Continuous Turn 선택 가능      |
| 무기 집기/발사 | Grab → Trigger                         |
| 상호작용     | 버튼 가까이 → Trigger                       |
| 장착       | 특정 태그 오브젝트만 장착 가능                      |
| UI 조작    | 레이 기반 선택 + 트리거 클릭                      |
| 파괴       | `MeteorPistol`로 발사 → `Breakable` 대상 파괴 |

---

## 실행 방법

1. Unity 2022 이상에서 프로젝트 열기
2. **XR Interaction Toolkit 세팅 필요**
3. XR 디바이스 연결 후 `Main Scene` 실행
4. ▶ 버튼 클릭 → 씬 시작 → VR 컨트롤러로 상호작용 진행

---

## 대표 시스템 구현 방식

### 씬 전환 시스템

* `SceneTransitionManager` + `FadeScreen` 조합으로 몰입도 높은 전환 제공
* 컷씬 흐름은 `PlayableDirector`를 통해 연출 제어

### 사운드 시스템

* 모든 오디오 재생은 `AudioManager` 중심
* UI 이벤트(`UIAudio.cs`), 버튼/문(`PlayAudioFromAudioManager.cs`) 등 상황별 분리

### 설정 저장

* `PlayerPrefs` 기반 회전 방식 저장
* `SetTurnTypeFromPlayerPref.cs`에서 불러와 적용

---

## 향후 개선 사항

* 음성 더빙 및 자막 시스템 추가
* 사용자 선택에 따른 분기형 스토리 구조 구현
* 다국어 지원 (한글/영어 UI)
* 햅틱 연출 보강 및 조명 기반 연출 강화
* 퍼즐 시스템 도입 (소켓 조립, 연쇄 트리거 등)

---

## 라이선스

```
MIT License

본 프로젝트는 자유롭게 사용/수정/배포 가능하며, 상업적 사용 시 출처 표기를 권장합니다.
```

---

## 시연 영상 다시 보기

[![Demo Video](https://img.youtube.com/vi/hvpG1fLjlkE/maxresdefault.jpg)](https://youtu.be/hvpG1fLjlkE)

[https://youtu.be/hvpG1fLjlkE](https://youtu.be/hvpG1fLjlkE)
