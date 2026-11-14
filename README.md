# 2026_koongya_roblox
2026 koongya roblox game contest

ReplicatedStorage
├─ Shared (Folder)
│  ├─ Config            [ModuleScript] 인원수, n초/n포인트 등 밸런스 수치 전부
│  ├─ Enums             [ModuleScript] RoundState, PlayerState, Role, SeekerClass
│  ├─ SeekerClasses     [ModuleScript] 양파/주먹밥/샐러리/무시 쿵야 능력 정의
│  ├─ Util              [ModuleScript] Signal, 거리계산, 타이머 등
│  └─ Net               [ModuleScript] RemoteEvent 래퍼 (검증/레이트리밋 포함)
└─ Remotes (Folder)     RemoteEvent / RemoteFunction 모음

ServerScriptService
├─ Main                 [Script] 부팅: 서비스 로드 및 초기화 순서 관리
└─ Services (Folder, 전부 ModuleScript)
   ├─ DataService       플레이어 데이터(포인트, 보유 쿵야) 저장/로드
   ├─ LobbyService      로비 대기, 최소 인원 체크, 로비 스폰
   ├─ RoundService      ★ 게임 상태머신 (전체 흐름 지휘)
   ├─ RoleService       술래/식재료 랜덤 배정, 스폰, 캐릭터 모델 적용
   ├─ IngredientService 재료 랜덤 스폰, 획득/운반/드랍, 제출, 목표 달성
   ├─ EscapeService     탈출구 개방, 탈출 처리
   ├─ CombatService     술래 평타(맑눈광 빔) 판정, 피격 2회→기절
   ├─ CaptureService    기절자 운반, 운반 취소, 조리대 배치 요청
   ├─ CookingService    조리대 게이지, 조리기구, 타이머, 탈락/풀려남
   ├─ RescueService     밸브 구출, 구출 가능 조건 검증
   ├─ AbilityService    술래 캐릭터 능력 (쿨타임, 패시브)
   ├─ ScreamService     비명 (스페이스 연타, 거리 내 전달)
   ├─ PointService      포인트 적립/정산 (중복 방지 포함)
   ├─ SpectateService   탈락자 관전 대상 목록/제한
   └─ ShopService       쿵야 클래스 구매 검증

ServerStorage
├─ Maps                 맵 모델 (라운드 시작 시 Workspace로 복제)
├─ IngredientModels     식재료 오브젝트 템플릿 (종류별)
└─ SeekerModels         술래 캐릭터 모델 4종

StarterPlayer
└─ StarterPlayerScripts
   ├─ ClientMain        [LocalScript] 컨트롤러 부팅
   └─ Controllers (ModuleScript)
      ├─ InputController     마우스 평타, 스페이스/마우스 연타 입력 전송
      ├─ HudController       상태/재료 수/타이머/쿨타임 표시
      ├─ ScreamController    비명 사운드 재생 (거리 감쇠)
      ├─ AbilityController   술래 능력 키 입력, 탐지 연출
      ├─ SpectateController  관전 카메라
      ├─ ShopController      상점/캐릭터 선택 UI
      └─ ResultController    결과 화면, 포인트 표시

StarterGui
└─ ScreenGui들: HUD, 조리 게이지, 구출 게이지, 결과, 관전 선택, 상점, 로비 대기

Workspace (맵 태그 규칙)
   IngredientSpawn / SubmitZone / ExitDoor / ExitPoint
   CookStation / Cooker / Valve
   SeekerSpawn / SurvivorSpawn / LobbySpawn
