# Reference

* [What's the difference between a console, a terminal, and a shell?](https://www.hanselman.com/blog/whats-the-difference-between-a-console-a-terminal-and-a-shell)
* [Introducing the Windows Pseudo Console(ConPTY)](https://devblogs.microsoft.com/commandline/windows-command-line-introducing-the-windows-pseudo-console-conpty/)
* [Difference Between Kernel and Shell](https://jaguhiremath62.medium.com/difference-between-kernel-and-shell-718b3de15be6)

# Terminal

* `Terminate` 단어에서 유래하여 프로세스의 종료 또는 `터미널`의 끝을 나타낸다.
* `TTY` 또는 `Teletypewriter`가 최초의 터미널이었다.
* 소프트웨어적인 의미에서 터미널은 `TTY` 또는 터미널의 소프트웨어 환경을 의미한다.
  * 쉘을 래핑한 프론트엔드 프로그램이라고 할 수 있다.
* 텍스트 출력에 특화되어 있고 해당 입력의 의미는 생각하지 않는다.
* `시리얼 또는 소켓을 통한 컴퓨터나 전용 장치의 원격 세션` 이라는 의미로도 사용한다.

# Console

* 20세기 중반의 사람들이 거실에 `콘솔` 또는 `콘솔 캐비닛` 이라는 가구를 가지고 있었다.
* 컴퓨터 문맥 상 콘솔은 화면과 키보드가 결합된 콘솔 또는 캐비닛을 의미한다.
* 소프트웨어적 의미로 터미널과 콘솔은 동의어다. 요새는 `물리적으로 연결되어 있는 입출력도구` 라는 의미로도 사용한다.
  * = physical terminal

# Shell

* 터미널이 받은 입력을 OS에 보내는 프로그램이다.
* 입력을 받으면 쉘은 출력을 생성하여 디스플레이를 위해 다시 터미널에게 전달한다.
* `bash`, `tsch`, `sh`, `PowerShell`, `pwsh`, `cmd`, `yori`, `4dos` 등이 있다.
* 쉘의 선택이 터미널 응용프로그램의 선택을 강요하지 않는다. 즉, 독립되어 있다.
  * 터미널은 쉘을 사용하지만, 쉘은 터미널 없이 동작 가능하다.
* OS 서비스를 유저에게 보여주는 인터페이스 (다른 정의)
  * Internet Explorer도 shell의 한 종류?

# Command Line, and Shell

* `Command-Line` 또는 `CLI(Command Line Interface/Interpreter)` 는 사람이 컴퓨터를 사용하는 가장 기본적인 메커니즘을 말한다.
  * 입력을 받아들이고 요청된 명령을 수행한다.
* 점점 더 정교한 일을 하는 명령어를 처리하기 위해서 커맨드라인 프로세스가 `shells` 으로 진화했다.
* 오리지날 `UNIX shell(sh)`은 `Korn shell(ksh)`, `C shell(csh)`, `Bourne shell(sh)`에게 영향을 주었으며 `Bourne Again shell (bash)`의 시초가 되었다.
* `Microsoft` 시리즈들에서는 아래와 같이 변경되었다.
  * `MS-DOS(command.com)`는 비교적 단순한 커맨드라인 쉘이다.
  * `Windows NT`의 `명령 프롬프트(cmd.exe)`는 기존 `MS-DOS`와 호환되면서 강력한 OS를 위한 몇가지 추가 명령을 가지고 있다.
  * 2006년에 `.NET CLR, .NET Framework` 기능을 기반으로 구축한 오브젝트 기반 커맨드라인 쉘 `Windows PowerShell`이 출시되었다.
    * 파일/스트림 기반이 아니라 객체 지향 쉘이다.
    * 텍스트 스트림 대신 객체 스트림을 처리하여 많은 스크립트를 작성하고 유지, 관리할 필요가 없다.
  * 2016년에 `Windows Subsystem for Linux (WSL)`을 출시하여 리눅스 바이너리를 윈도우에서 직접 실행할 수 있도록 만들었다.
    * 이중 부팅이나 가상 머신을 사용하지 않고도 리눅스 커맨드라인 툴을 사용할 수 있다.

# Modern Command-Line

* 여전히 예전에 사용하던 기계식 텔레타이프 머신과 동일한 기능들을 수행한다.
* 하지만 느린 TTY 시리얼 통신 회선 대신 프로그램들은 매우 빠르고 메모리 안에 있는 `Pseudo Teletype (PTY)` 통신을 통해 데이터를 주고받는다.
* 주로 로컬에서 실행되는 커맨드라인 프로그램과 통신하지만, 로컬 네트워크나 인터넷을 통해 원격 컴퓨터와 통신할 수 있다.

# Pseudo Console, Pseudo Terminal, PTY, Pseudo TTY (ConPTY)

* 터미널을 에뮬레이트하는 터미널 에뮬레이터 또는 소프트웨어 인터페이스
* 