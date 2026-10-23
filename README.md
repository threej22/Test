# SpeakerCheck 0.2.0

PC에서 1 kHz를 재생하고, 스피커 소리를 수집한 디바이스의 PC 오디오 입력을 자동 녹음하여 SoX로 판정하는 Windows 데스크톱 도구입니다.

## 다운로드

[**SpeakerCheck 0.2.0 소스 ZIP 다운로드**](https://github.com/threej22/Test/raw/refs/heads/main/SpeakerCheck-0.2.0-source.zip)

[최신 ZIP](https://github.com/threej22/Test/raw/refs/heads/main/SpeakerCheck-source.zip)

압축을 풀고 `SpeakerCheck/setup.bat` → `start.bat` 순서로 실행합니다. Python 3.11 이상과 별도 SoX 설치가 필요합니다. 기존 버전 사용자는 `setup.bat`를 다시 실행하세요.

## 자동 녹음 · 양산 검사

1. 설정에서 `sox.exe` 지정.
2. **자동 녹음 · 양산 → 장치 새로고침**, PC 스피커 출력/디바이스 PC 입력 선택.
3. 채널, 출력 레벨, 안정화/녹음 시간, 필요 시 SPL 교정 설정.
4. **1 kHz 검사 항목 적용** 후 Spec 관리에서 실제 제품 기준을 설정·확인.
5. 제품번호/작업자/스테이션/저장 폴더 입력 → **자동 녹음 → 판정**. 바코드 Enter 지원.
6. **제품별 시험 이력**에서 제품 검색/CSV 저장/보고서 JSON 저장.

**1 kHz 연속 재생**을 먼저 켜면 성공한 검사 후에도 재생을 유지합니다. 상단 오디오 중지 또는 Esc로 종료합니다. 무음 옵션은 톤을 잠시 멈춰 Noise/SNR을 측정합니다.

디바이스는 Windows 표준 녹음 장치로 인식되어야 합니다. 독자 UART/USB packet 프로토콜은 지원하지 않습니다. 정해진 시간 녹음 후 판정하며 무기한 실시간 판정이나 PLC 트리거는 포함하지 않습니다.

## 양산 Log

- 제품번호 필수, 검사마다 고유 Run ID. 시작 전에 RUNNING 기록.
- SQLite `production.sqlite3`: 제품/작업자/시각/Spec/장치/교정/설정/측정값/판정/사유/원본 SHA256 및 전체 보고서 JSON.
- KST 날짜별 WAV 자동 저장과 `events.jsonl` 작업 로그.
- 최종 로그 commit 후에만 PASS 표시. 중단 ABORTED, 오류 ERROR, 비정상 종료 RUNNING은 합격 아님.
- CSV는 제품별 주요 측정값 컬럼을 제공하며 JSON은 전체 상세 보고서입니다.

기존 WAV 분석, RMS/Peak/클리핑/THD/Noise/SNR/좌우차/교정 SPL/기준 대비 주파수 응답, 그래프, JSON/CSV 저장도 포함합니다. 고정 1 kHz만으로 전체 주파수 응답을 측정할 수는 없습니다. 기본 Spec은 예시입니다.

## 검증 범위

테스트 **63개 통과**. Linux에서 합성 오디오 backend와 실제 SoX/SQLite/Qt offscreen으로 검증했습니다. **실제 Windows 오디오 장치 연결과 EXE 빌드는 미검증**입니다. 실제 양산 라인에서 장치/교정/지연/장애 조건을 확인해야 합니다.

ZIP SHA256: `0d535023eafd68bb83ceef4dce8185539762e380fa8baeb72be632f032fb8107`
