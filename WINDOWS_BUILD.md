# Windows 64비트 EXE 한 파일로 로컬 빌드

이 ZIP은 **빌드용 소스**입니다. 빌드 PC에만 Python 3.12 64비트와 인터넷 연결이 필요합니다.

1. ZIP 전체를 쓰기 가능한 새 폴더에 압축 해제합니다.
2. `build_windows.bat`을 실행합니다.
시연용 WAV는 빌드 과정에서 자동 생성하므로 빌드 키트에는 포함하지 않습니다.

3. 파일 선택 창에서 기존 `sox.exe`를 선택합니다. 원래 배포본의 DLL·라이선스 파일과 함께 있는 exe를 선택하세요.
4. 빌드와 자체 검증이 성공하면 아래 **EXE 한 파일**을 배포합니다.

```text
output/SpeakerCheck-0.4.3-windows-x64.exe
```

압축해서 전달하려면 `output/SpeakerCheck-0.4.3-windows-x64-single-exe.zip`을 사용하세요. 이 ZIP 안에도 `SpeakerCheck.exe` 한 파일만 있습니다. `dist/SpeakerCheck.exe`는 빌드 중간 결과이며, **자체 검증을 통과한 최종 파일은 output에 생성**합니다.

명령 프롬프트에서 SoX 경로를 직접 지정할 수도 있습니다.

```bat
build_windows.bat "D:\tools\sox\sox.exe"
```

배포 PC는 **EXE만 실행**합니다. Python·pip·setup.bat·SoX 설치나 별도 DLL/lib 폴더가 필요 없습니다. Python 런타임, Qt, NumPy/SciPy/Matplotlib, PortAudio, SoX 실행 파일과 인접 DLL, 라이선스를 EXE에 포함합니다. Windows 운영체제나 오디오 장치 드라이버 자체는 포함하지 않습니다. 대상은 Windows 10/11 64비트이며 마이크 권한은 필요합니다.

내부 파일은 실행 시 Windows 사용자 임시 폴더에 자동 추출하므로 시작이 조금 느릴 수 있습니다. 녹음 WAV·SQLite 로그는 기존 사용자 결과 폴더에 저장하며 임시 추출 폴더와 별개입니다.

실패하면 창이 유지되고 `setup.log` 또는 `build.log`에 원인이 남습니다. 빌드 스크립트는 EXE만 한글 이름의 빈 폴더에 복사하고 Python을 PATH에서 제외한 환경에서 일반 Windows GUI/offscreen, PortAudio, 내장 SoX, 1kHz PASS/혼합톤 FAIL, SQLite 검증을 수행합니다. 실제 스피커·디바이스의 음향 검증은 별도입니다.

소스 테스트는 Linux에서 수행했습니다. 네이티브 Windows 단일 EXE 빌드·검증은 사용자의 로컬 빌드에서 실행됩니다.
