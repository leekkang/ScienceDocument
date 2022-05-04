# Cygwin

  - `UNIX` 프로그램이 Windows 시스템에서 아무런 변경이나 수정 없이 컴파일 및 실행될 수 있도록 도와주는 라이브러리

  - 일종의 가상머신으로 윈도우 위에 `POSIX` 레이어를 얹은 방식이다. (무겁다)
  - 컴파일된 `UNIX` 도구 및 응용 프로그램 세트
  - `UNIX` 터미널을 실행 가능하다.
  - `Linux` 에서 사용 가능한 모든 응용 프로그램을 `Windows` 사용자에게 제공하는 것을 목표로 한다.
  - `Cgywin` 응용 프로그램은 모든 응용 프로그램에 링크되어야 하는 `cygwin.dll` 을 사용해야 한다.
    - 응용 프로그램과 함께 `cygwin.dll`을 배포할 수 있지만 진정한 네이티브는 아니다.
    - `Windows API` 와 함께 이 계층을 사용하면 잠재적으로 속도가 느려지고 기능에 제한이 생길 수 있다.
  - 윈도우 10에서는 [Windows Subsystem for Linux(WSL)] 를 사용할 수 있기 때문에 중요도가 떨어졌다.

---
# MSYS (Minimal SYStem)

  - `bash`, `make`, `gawk` 및 `grep` 과 같은 `GNU` 유틸리티 모음
    - `bash(Bourne Again SHell)` 와 유사한 쉘 스크립트를 실행하기 위한 환경으로 사용된다는 점을 제외하면 `Cygwin`의 변형처럼 보인다.

  - `UNIX` 도구에 의존하는 응용프로그램을 만들 수 있다.
  - `MinGW`와 `cmd shell` 의 결함을 보완하기 위해 만들어짐
  - `Cygwin` 에서 파생되어 나옴 (`msys.dll`이 `cygwin.dll`의 파생 버전)

---
# MinGW (Minimalist GNU for Windows)

  - 단순히 `GCC, Make, Bash` 등과 같은 `GNU` 컴파일러 도구의 `Windows` 포트를 위해 만들어짐
  
  - `Windows` 에서 `GCC` (GNU 컴파일러) 및 소수의 도구를 사용하는데 필요한 최소한의 환경을 제공
  - `Cygwin` 과 같은 `Unix` 에뮬레이션 계층이 없음.
  - 본질적으로 `Microsoft Visual C++` 컴파일러와 `linking/make` 도구의 대체재
    - `GNU` 컴파일러 도구 제품군을 사용해서 크로스 컴파일을 할 수도 있지만 `.exe`, `.dll` 파일들을 포함하는 기본 `Windows x86` 타겟으로 컴파일된다.
  - `Cygwin 1.3.3` 에서 파생되어 나옴
  - 윈도우 환경을 그대로 유지하되 리눅스 명령어만 사용해야 할 경우 (ex: 오픈소스 라이브러리 빌드) 유용하게 사용할 수 있다.
 
--- 
# GnuWin32

  - `GNU` 도구들을 Windows로 이식한 것
  - `MSYS`와 마찬가지로 `msvcrt.dll`과 추가 라이브러리를 사용하여 일부  `UNIX` 호환성 기능을 제공한다.
  - `Windows` 프로그램과 batch 파일이 일부 `GNU` 프로그램과 라이브러리를 직접 사용할 수 있도록 한다.

---
# GOW (Gnu On Windows)

  - GnuWin32 하위호환

---
# Difference & Intent

  `Cygwin` 은 `Windows OS`에서 `UNIX`를 쓰고싶을 때, 

  `MSYS`는 `GNU / UNIX` 빌드 도구를 사용하여 `Windows` 프로그램을 빌드할 때, 

  `GnuWin32` 는 개별 `GNU` 프로그램 및 라이브러리를 `Windows` 로 포팅할 때 사용


---
# 참고

  - [Cygwin-Mingw-MSYS-GnuWin32](http://poquitopicante.blogspot.com/2012/08/cygwin-mingw-msys-gnuwin32-gnu.html)
  - [MinGW vs MSYS](https://gist.github.com/ReneNyffenegger/a8e9aa59166760c5550f993857ee437d)
  - [Cygwin vs Mingw](https://stackoverflow.com/questions/771756/what-is-the-difference-between-cygwin-and-mingw)
  - [Cygwin vs GnuWin32](https://stackoverflow.com/questions/10712550/difference-between-gnuwin32-and-cygwin)


[Windows Subsystem for Linux(WSL)]: https://namu.wiki/w/%EC%9C%A0%EB%8B%89%EC%8A%A4/MS%20%EC%9C%88%EB%8F%84%EC%9A%B0