# NADIR TRACE 그래픽 목록

기준: v0.49.2. src/nadir_trace.c, src/lobby_background.h의 데이터를 사용했습니다.
게임 소스·실행파일·저장 데이터는 변경하지 않았습니다.

## 파일 안내

| 파일 | 내용 |
| --- | --- |
| 01_palette.png | 게임의 이름 있는 색상 23개와 로비 원본 팔레트 5개. RGB HEX 표기 |
| 01_palette_lobby.png / .gif | 로비 팔레트의 기본값·최저·최고 밝기와 호흡 |
| 02_objects.png / .gif | 지형, 앵커, 게이트, 시야 밖 오브젝트 |
| 02_world_states.png | 3개 구역의 바닥·벽·격자와 기억된 지형 |
| 03_characters.png / .gif | 플레이어, 적 8종, 피격·WARDEN·BEYOND 합성 예시 |
| 04_items.png / .gif | 아이템 6종과 인벤토리 표시 |
| 05_attack_glyphs.png / .gif | 방향별 투사체, 먼지 전조, 경고, 장판 |
| 06_attack_patterns.png / .gif | LANCER·RELAY·PRISM·BLOOM 공격 범위. DANGER 0/6 비교 |
| 06_field_lifecycle.png | 장판의 TTL별 모양·색상. TTL 1은 피해 없음 |
| 07_projectile_paths.png / .gif | 16방향 이동 중 4방향 예시. 발사 전·진행 중 전조 |
| 08_ui_glyphs.png / .gif | HP·HUNGER·ATK·RANK·무한대·BOOST |
| 08_shield_parts.png | 실드 구성 조각 8개와 스파크 |
| 08_shield_and_radar.png / .gif | 실드 합성, 피해 방어, 레이더 상태 |
| 08_hud_feedback.png / .gif | 랭크업·스탯 증가·XP·경고색·wiggle·메뉴 밑줄 |
| 09_font_5x7.png | 일반 글꼴 47개. 공백 포함 |
| 10_keycap_font_5x5.png | 축약 키캡 글꼴. 숫자 4의 전용 패턴 포함 |
| 10_key_labels.png | 실제 사용되는 키 라벨 |
| 11_other_and_unused.png / .gif | 미사용 스프라이트와 사용되지 않는 대체 프레임 |
| 12_lobby_background.png / .gif | 5색 로비 배경과 호흡·설비 점멸 |
| raw/ | 원본 크기 투명 PNG, 기본·대체 프레임, 글리프 데이터 |
| palette.csv / palette.json | 색상 값과 로비 밝기 조절 범위 |
| manifest.json | 원본 SHA-256, 생성 파일 목록, 프레임·검증 정보 |

## 표기와 애니메이션

- 영문 라벨은 게임의 5×7 글꼴입니다. 새로 그린 아이콘은 없습니다.
- 카드형 PNG는 A/B 프레임을 나란히 표시합니다. 정적 항목은 같은 그림을 두 번 표시합니다.
- 카드형 GIF는 게임의 통상 주기인 프레임당 400ms입니다. 시스템 타이머 오차와 카운터 순환에 따른 간격 차이는 생략했습니다.
- 공격 범위·투사체 GIF는 입력에 따른 진행을 400ms 간격으로 예시한 것입니다. 게임에서 턴이 자동으로 흐른다는 뜻은 아닙니다.
- 공격 범위는 벽이 없는 **21×21칸 시야의 일부**입니다. 장거리 공격의 전체 사거리를 나타내지 않습니다.
- HUD GIF는 20ms 게임 타이머를 2틱씩, 로비 GIF는 실제 배경 갱신 간격인 4틱씩 샘플링했습니다. GIF 재생기는 짧은 지연을 다르게 처리할 수 있습니다.
- 로비 PNG는 원본 5색입니다. GIF는 호흡에 따라 중간 3색의 RGB를 -7~+8 조절합니다. 점멸까지 포함한 반복 길이는 10.24초입니다.
- GIF는 디더링 없이 고정 팔레트를 사용합니다. 저장 전 RGB가 손실되지 않는지 확인합니다.
- 모든 확대는 최근접 보간입니다. 시트에서는 8×8 아이콘이 보통 64×64픽셀로 표시됩니다.

## 원본 데이터와 실제 표시의 차이

- TREE와 BEYOND_TREE는 대체 프레임이 있지만 맵에서는 정적으로 표시됩니다.
- LANCER 이후 ID의 애니메이션은 저장된 대체 프레임을 사용하지 않고 각 행의 비트를 왼쪽으로 한 칸 순환시킵니다. 이 규칙을 그대로 적용했습니다.
- BEACON·SHARD는 현재 렌더러에서 사용하지 않는 스프라이트입니다. 별도 시트의 색은 식별용 COLOR_TEXT입니다.
- raw/sprites/*_stored_alt.png는 배열에 저장된 대체 프레임입니다. *_display_b.png는 분류한 실제 표시 규칙으로 만든 B 프레임입니다. 미사용 두 스프라이트는 배열 미리보기입니다.
- 원본 크기 파일은 역할별 색상 변형 전체를 복제하지 않습니다. 색상 변형은 분류 시트를 참고하세요.
- WARDEN은 별도 몬스터 도안이 아니라 적 위에 ANCHOR를 합성합니다. 시트는 BULWARK를 예로 들었습니다.
- 실드 스파크는 프레임과 턴 수로 위치가 달라집니다. GIF에는 8턴의 조합을 넣었습니다.
- WINDOW ICON은 PLAYER 기본 프레임을 16×16으로 확대한 것입니다. 카드 시트에서는 다른 아이콘과 같은 크기로 비교하고, raw/window_icon_16x16.png에 원본 크기를 저장했습니다.
- 컷씬 전체 화면·패널 레이아웃·문장 전체는 개별 글리프 목록에 포함하지 않았습니다. 같은 글꼴·스프라이트·직선·사각형을 조합하는 화면입니다.

## 다시 생성

프로젝트 루트에서 Pillow가 설치된 Python으로 실행합니다.

~~~powershell
python scripts/export-visual-catalog.py
~~~

기본 출력 폴더는 art-reference/입니다. 다른 폴더는 --out 경로로 지정합니다.
이 도구가 생성한 폴더 또는 빈 폴더에만 출력합니다. 기존 파일을 임의로 삭제하지 않습니다.
