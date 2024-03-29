
# ScienceDocument

- 개인적인 궁금증을 정리해놓은 저장소.

1. ## [Windows Terminal](WindowsTerminal.md)
   
2. ## [About Console, Terminal and Shell](AboutConsole,TerminalandShell.md)
3. ## [About GNU Programs in Windows](Gnu프로그램비교.md)
4. ## [About Bash Commands](AboutBashCommands.md)
5. ## [Git Commands](유용한%20Git%20커맨드.md)


- `Windows Terminal` 을 컨텍스트 목록에 추가하는 레지스트리
  - [add context WT](contextTerminal.reg)
  - [delete context WT](contextTerminalDelete.reg)
  - [add context VSCode](contextVSCode.reg)
  - [delete context VSCode](contextVSCodeDelete.reg)
  
- 레지스트리 코드 편집 방법 공부할 것
  - https://stackoverflow.com/questions/3681032/set-icon-for-custom-right-click-context-menu-item-for-all-desktop-shortcuts-win
  - https://stackoverflow.com/questions/20449316/how-add-context-menu-item-to-windows-explorer-for-folders
  - https://luvery93.github.io/articles/2018-10/windows10-open-a-command-prompt-in-any-folder-from-the-right-click-context-menu

- OOP의 5대 원칙
  - https://bozeury.tistory.com/entry/OOP%EC%9D%98-5%EB%8C%80-%EC%9B%90%EC%B9%99?category=826469

- C와 C#의 차이
  - https://bozeury.tistory.com/entry/C%EC%99%80-C%EC%9D%98-%EC%B0%A8%EC%9D%B4?category=826469

- 컴파일러 최적화 종류와 기법 
  - https://bloofer.tistory.com/14

- Makefile 강좌
  - http://doc.kldp.org/KoreanDoc/html/GNU-Make/GNU-Make.html#toc8
  - https://www.youtube.com/watch?v=jnJL6ppn26Q

- C언어 표준함수 헤더 파일, 소스 위치
  - 헤더 위치 : `C:\Program Files (x86)\Windows Kits\10\Include\10.0~(SDK버전)\ucrt`
  - 소스 위치 : `C:\Program Files (x86)\Windows Kits\10\Source`
  - 참조 : https://blog.naver.com/tipsware/221275585536



---
# 빌드 시간 단축방법

  - [MP(Multicore-Process) 옵션을 통한 빌드 시간 단축](https://learn.microsoft.com/en-us/cpp/build/reference/mp-build-with-multiple-processes?view=msvc-170)
    - 컴파일러가 별도의 프로세스에 하나 이상의 자체 복사본을 만들어 동시에 소스 파일을 컴파일 한다.
    - `C/C++ -> 코드 생성 -> 최소 다시 빌드 가능` 옵션을 해제해야 한다.
      - 더 이상 사용되지 않는 옵션이다. [문서](https://learn.microsoft.com/ko-kr/cpp/build/reference/gm-enable-minimal-rebuild?view=msvc-170)
    - `옵션 -> 프로젝트 및 솔루션 ->VC++ 프로젝트 설정` 탭에 사용가능한 프로세스 수를 지정할 수 있다. 0은 가능한 모든 프로세스를 사용한다는 것이다. (== `/MP number`)
    - [가이드](https://learn.microsoft.com/ko-kr/visualstudio/msbuild/using-multiple-processors-to-build-projects?view=vs-2022)
  
  - [증분 링크(Incremental Linking)](https://learn.microsoft.com/en-us/cpp/build/reference/incremental-link-incrementally?view=msvc-170)
    - 링킹 과정에서 필요한 `메모리 배치, 함수 순서, 코드/데이터 영역 계산 시간`을 줄이기 위해 수정된 것만 재계산하는 방식
    
    - 후속 증분 링크, 증분 링크된 실행파일, 라이브러리 파일 등을 대비하기 때문에 미증분된 프로그램보다 크기가 크다. (패딩 적용)
    - `링커 -> 일반 -> 증분 링크 사용` 옵션으로 적용 가능하다.
    - 2022 버전에는 기본적으로 디버그 모드에서는 켜져있다.
    - 가끔 빌드가 꼬일 때가 있는데 리빌드 하면 된다.
  
  - [유니티 빌드(Unity Build, Jumbo Build)]()
    - 여러 개의 컴파일 단위(`Translation Unit`)들을 하나의 단위로 묶어 프로젝트 컴파일 속도를 높이는 방법이다.
    
    - 주로 `#include` 지시문을 사용하여 여러 개의 소스파일을 하나의 큰 파일로 묶어서 수행한다.
    - 중복되는 헤더 파일들의 컴파일 횟수가 상당히 줄어들며, 오브젝트 코드 개수가 줄어들기 때문에 해당 파일 내에서 프로시저 간 분석 및 최적화가 가능하다.
    - 단점으로는, 메모리 사용량이 커진다는 것, 일부 구문의 충돌(static 같은), 동일한 이름의 함수를 정의하는 것, 매크로 정의 충돌 등이 있다.
    - 오브젝트 파일이 너무 커지면 [C1128 에러](https://learn.microsoft.com/ko-kr/cpp/error-messages/compiler-errors-1/fatal-error-c1128?view=msvc-170)가 발생할 수 있다. 명령줄에 `/bigobj` 명령을 추가하면 해결된다.
    - 메모리 관련 문제 해결을 위해 `속성 -> 고급 -> 기본 설정 빌드 도구 아키텍처`를 64비트로 바꾸면 해결된다.
    - 수정이 힘든 파일은 `C/C++ -> Unity 빌드 -> Unity 파일에 포함` 옵션을 사용하여 유니티 빌드에서 제외하면 된다.
    - 협업하는 경우 `include 누락`(외부에서 빌드 파일 구성이 변경되는 경우)을 조심해야 한다.

  - 참고
    - http://egloos.zum.com/sweeper/v/3051658
    - https://blueasa.tistory.com/587
    - https://imitursa.tistory.com/4368

---
# [윈도우 환경변수 문자열 종류](https://badayak.com/entry/%EC%9C%88%EB%8F%84%EC%9A%B010-%ED%99%98%EA%B2%BD%EB%B3%80%EC%88%98-%EB%AC%B8%EC%9E%90%EC%97%B4-%EC%A2%85%EB%A5%98)

|       변수명        | 설명 
| :-----------------: | :----------------------------------------------------------------------------------- |
`%ALLUSERSPROFILE%` | C:\ProgramData 폴더 반환
`%APPDATA%` | C:\Users\사용자\AppData 폴더 반환. 응용 프로그램이 기본적으로 데이터를 저장하는 위치
`%CD%`        | 사용자 현재 폴더를 반환
`%CMDCMDLINE%`    | 현재 명령을 시작하는데 사용된 명령과 명령행 옵션을 반환
`%CMDEXTVERSION%`  | 현재 명령 프로세서 확장의 버전 번호를 반환
`%COMPUTERNAME%` | 컴퓨터 이름을 반환
`%COMSPEC%` | 시스템에 설졍된 명령행 프로세스의 정확한 경로를 반환
`%DATE%` | 현재 날짜를 반환. date /t명령과 같은 형식을 사용
`%ERRORLEVEL%` | 최근에 사용된 명령의 오류 코드를 반환. 일반적으로 0이 아닌 값은 오류를 표시
`%HOMEDRIVE%` | 사용자 홈 디렉터리에 연결된 로컬 워크스테이션 드라이브 문자를 반환
`%HOMEPATH%` | 사용자 홈 디렉터리의 전체 경로를 반환
`%HOMESHARE%` | 사용자의 공유 홈 디렉터리의 네트워크 경로를 반환
`%LOGONSEVER%` | 현재 로그온 세션을 확인한 도메인 컨트롤러 이름을 반환
`%NUMBER_OF_PROCESSORS%` | 컴퓨터에 설치된 프로세서의 수를 표시
`%OS%` | 운영 체제 이름을 반환. 윈도우10은 운영 체제를 Windows_NT로 표시
`%PATH%` | 실행 파일을 검색할 경로를 지정
`%PATHEXT%` | 운영 체제에서 실행 가능하다고 간주되는 파일 확장명 목록을 반환
`%PROCESSOR_ARCHITECTURE%` | 프로세서의 칩 아키텍처를 반환. AMD 64비트 시스템의 경우 AMD64 반환
`%PROCESSOR_IDENTFIER%` | 프로세서의 설명을 반환
`%PROCESSOR_LEVEL%` | 컴퓨터에 설치된 프로세서의 모델 수를 반환
`%PROCESSOR_REVISION%` | 프로세서의 수정 버전 번호를 반환
`%PROMPT%` | 명령 프롬프트 설정을 반환
`%RANDOM%` | 0에서 32767까지 수 중에서 임의의 10진수를 반환
`%SYSTEMDRIVE%` | 루트 디렉터리(시스템 루트)가 있는 드라이브를 반환
`%SYSTEMROOT%` |  C:\Windows처럼 루트 디렉터리의 위치를 반환
`%TEMP%`, `%TMP%` | 시스템 및 사용자 현재 로그온한 사용자가 사용할 수 있는 응용 프로그램이 사용하는 기본 임시 디렉터리를 반환. 일부 응용 프로그램에는 TEMP가 필요하고 다른 프로그램은 TMP가 필요함
`%TIME%` | 현재 시간을 반환. time /t명령과 같은 형식을 사용
`%USERDOMAIN%` | 사용자 계정을 포함한 도메인 이름을 반환
`%USERNAME%` | 현재 로그온한 사용자 이름을 반환
`%USERPROFILE%` | 현재 사용자의 프로필 위치를 반환
`%WINDIR%` | C:/Windows처럼 운영 체제가 설치된 폴더의 경로를 반환