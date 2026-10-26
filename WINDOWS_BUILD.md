# Windows 64비트 로컬 빌드

이 ZIP은 **빌드용 소스**입니다. 빌드 PC에만 Python과 인터넷 연결이 필요하며, 배포받는 PC에는 설치하지 않습니다.

1. Windows 64비트 빌드 PC에 Python 3.12 64비트를 설치합니다. Python Launcher 또는 PATH 등록을 포함합니다.
2. ZIP 전체를 쓰기 가능한 새 폴더에 압축 해제합니다.
3. `build_windows.bat`을 실행합니다. 필요한 패키지와 빌드 도구를 설치하고 EXE를 만듭니다.
4. 파일 선택 창에서 기존의 `sox.exe`를 선택합니다. 원래 SoX 배포 폴더의 DLL·라이선스 파일과 함께 있는 exe를 선택하세요.
5. 빌드와 자체 검증이 성공하면 `output/SpeakerCheck-0.4.2-windows-x64-portable.zip`을 배포합니다.

명령 프롬프트에서 경로를 직접 지정할 수도 있습니다.

```bat
build_windows.bat "D:\tools\sox\sox.exe"
```

배포 PC: ZIP을 전부 압축 해제하고 `SpeakerCheck/SpeakerCheck.exe`를 실행합니다. Python·pip·setup.bat·SoX를 따로 설치할 필요가 없습니다. **EXE 옆 DLL과 tools 폴더를 함께 유지하세요.** 대상은 Windows 10/11 64비트입니다. 오디오 장치 드라이버와 마이크 권한은 필요합니다.

설치/빌드가 실패하면 창이 유지되고 원인과 로그 위치를 표시합니다. 설치 로그는 `setup.log`, 빌드 로그는 `build.log`입니다. 빌드 스크립트는 실행 파일을 추출한 뒤 Python을 PATH에서 제외한 환경에서 일반 Windows GUI와 offscreen Qt·PortAudio·포함된 SoX·1kHz PASS/혼합톤 FAIL·SQLite 검증을 실행합니다. 물리 오디오 장치를 시험한 것은 아닙니다.

검증 범위: Linux 소스 테스트 통과. 첫 Windows 소스 검증에서 한글 WAV 경로 문제를 재현하고 파일 핸들로 전달하도록 수정했습니다. 수정 후의 네이티브 Windows 빌드 검증은 이 로컬 빌드 단계에서 실행됩니다. 원격 자동 빌드는 수동 실행으로 변경했습니다.
