# DanClient

Hypixel SkyBlock용 Fabric 클라이언트 모드예요.
미스릴 채굴, 드릴 연료 보충, 커미션 수령·이동, 슬레이어 커미션 사냥, 낚시를 자동으로 해줘요.

> ⚠️ 자동화 기능은 Hypixel 규칙상 매크로로 분류되어 제재를 받을 수 있어요. 사용에 따른 책임은 본인에게 있어요.

## 다운로드

**[최신 버전 받기](https://github.com/danmuzi0929/danclient-releases/releases/latest)** → `danclient-<버전>.jar`를 눌러 받아요.

버전별 변경 내용은 [Releases](https://github.com/danmuzi0929/danclient-releases/releases)에서 볼 수 있어요.

## 설치

| 필요한 것 | 버전 |
|---|---|
| Minecraft | 26.1.2 |
| Fabric Loader | 0.19.5 이상 |
| Fabric API | 26.1.2용 |
| Java | 25 이상 |

1. [Fabric Loader](https://fabricmc.net/use/installer/)로 Minecraft 26.1.2에 Fabric을 설치해요.
2. [Fabric API](https://modrinth.com/mod/fabric-api)의 26.1.2용 jar를 받아요.
3. 위에서 받은 `danclient-<버전>.jar`와 Fabric API jar를 `.minecraft/mods` 폴더에 넣어요.
4. Fabric 프로필로 게임을 켜요.

새 버전이 나오면 `mods` 폴더의 예전 `danclient` jar를 지우고 새 jar를 넣으면 돼요. 설정은 그대로 남아요.

## 사용법

- 게임에서 `/dan`을 입력하면 설정 메뉴가 열려요. 버튼에 마우스를 올리면 설명이 나와요.
- 키바인드: 옵션 → 조작 → 키 설정 → **DanClient**
  - Toggle Auto Mithril Mining
  - Toggle Auto Commission
  - Toggle Auto Fishing
- 설정은 `.minecraft/config/danclient.json`에 저장돼요.

## 기능

### Auto Mithril Mining
- 가장 가까운 미스릴 블록을 자동으로 조준해서 채굴해요. Titanium 커미션 중엔 티타늄을 먼저 캐요.
- 곡괭이·드릴·Gemstone Gauntlet을 Pickaxe Slot에 자동으로 장착해요.
- 곡괭이 능력 자동 사용, 채팅 중 채굴, 같은 블록을 못 캘 때 다른 블록으로 바꾸기(Retarget)를 지원해요.
- **Player Warp**: 다른 플레이어가 가까이 오래 있으면 `/warp home`으로 피했다가 돌아와요.
- **Macro Checking**: 서버가 강제로 텔레포트·회전시키면 멈추고 채굴 장소로 돌아와요.

### Mining Hud
- 드워븐 마인즈에 있을 때 화면에 미스릴 채굴 상태, 작동 시간, 마지막 매크로 체크 시각을 보여 줘요.
- `/dan` → Mining → Mining Hud에서 줄마다 켜고 끌 수 있어요.
- 위치와 크기는 `/dan` → General → **Edit Hud**에서 바꿔요. 맨 위 드롭다운(`Mining ▼`)으로 옮길 HUD를 고르고, 마우스로 끌어서 옮기거나 모서리를 끌거나 휠을 굴려 크기를 바꾼 뒤 Esc를 누르면 저장돼요.

### Auto Refuel
- 드릴 연료가 설정값 이하로 떨어지면 Abiphone으로 Jotraeline에게 전화해서 Volta로 연료를 채우고 채굴을 다시 시작해요.

### Auto Commission
- 완료된 커미션을 Royal Pigeon으로 수령하고, 다음 커미션 장소로 `/warpforge` + AOTV 텔레포트로 이동해요.
- 마이닝 커미션이면 도착 후 자동으로 채굴해요.
- **Slayer Commissions** 설정으로 슬레이어 커미션 사냥을 켜고 끌 수 있어요.

### 슬레이어 커미션 사냥
- Goblin / Glacite Walker를 찾아 가까운 몹부터 잡아요.
- 길찾기로 벽을 돌아가고, 반블럭·계단은 점프 없이 걸어서 올라가요.
- 갈 수 없는 몹은 건너뛰고 제자리에서 다른 몹을 찾아요.

### Auto Fishing
- 켜 둔 상태에서 직접 낚시찌를 던지면 시작해요. 입질 소리가 나면 자동으로 낚아 올리고 다시 던져요.
- 찌를 던진 뒤 15초 동안 입질이 없으면 찌를 걷어요.
- Reel Delay / Recast Delay로 낚아 올리기 전, 다시 던지기 전 기다리는 시간(ms)을 정할 수 있어요.
- **Auto Kill**: 바다 생물이 너무 많다는 메시지가 뜨면 Weapon Slot의 무기로 바꿔 바닥을 보고 우클릭한 뒤 낚시를 이어가요.
- **Work In Chat / Work In Inventory**: 채팅창이나 인벤토리를 열어 둔 채로도 계속 낚시해요.
- **Macro Checking**: 낚시 중에 서버가 강제로 텔레포트·회전시키면 Auto Fishing을 끄고 알려줘요.
- 손에 낚싯대가 없으면 꺼지지 않고 멈춰요. 다시 낚싯대를 들고 찌를 던지면 이어서 낚시해요.

### Fishing Hud
- 낚시 중에 화면에 Auto Fishing 상태, 작동 시간, 마지막 매크로 체크 시각을 보여 줘요.
- 낚시가 멈추면 5분 동안 더 보였다가 사라져요.
- `/dan` → Fishing → Fishing Hud에서 줄마다 켜고 끌 수 있고, 위치와 크기는 General → Edit Hud에서 `Fishing`을 골라 바꿔요.
