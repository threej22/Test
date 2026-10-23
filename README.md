# SpeakerCheck

SoX 기반 Windows 데스크톱 WAV 스피커 검증 도구입니다.

## 다운로드

[**SpeakerCheck-source.zip 다운로드**](https://github.com/threej22/Test/raw/refs/heads/main/SpeakerCheck-source.zip)

압축을 풀고 `SpeakerCheck` 폴더에서 `setup.bat` → `start.bat` 순서로 실행하세요. Python 3.11 이상과 별도 SoX 설치가 필요합니다. 실행 후 **설정 · 측정 안내**에서 `sox.exe`를 지정하세요.

포함: 한국어 UI, RMS/Peak/클리핑/THD/노이즈/SNR/좌우차/교정 SPL/기준 대비 주파수 응답, 제품 Spec 편집, PASS/NG, 그래프, JSON/CSV 저장, 합성 WAV 샘플, 테스트, Windows EXE 빌드 스크립트.

기본 Spec과 샘플 교정값은 예시입니다. 실제 제품 기준과 교정값으로 변경해야 합니다. Linux에서 실제 SoX 및 Qt offscreen 테스트 38개 통과. Windows 실기기 실행 및 EXE 빌드는 아직 검증하지 않았습니다.

ZIP SHA256: `5f91b7835d40fb412b4dc8e7fae612669ae4f178315957706ef30c6828b21a9f`
