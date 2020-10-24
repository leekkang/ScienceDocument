# Reference

* https://docs.microsoft.com/ko-kr/windows/terminal/

* 설정 버튼을 누를 때 `alt`를 누르면 `default.json` 파일이 켜진다.

* 아래의 설정들은 쓸만한 것만 코드로 썼다. 다른 설정이 필요하면 해당 탭의 메뉴얼을 확인하자.
* 값들은 디폴트로 지정되어 있는 값들이다.

# [글로벌 설정](https://docs.microsoft.com/ko-kr/windows/terminal/customize-settings/global-settings)

* 프로필 설정에 관계없이 모든 터미널 창에 영향을 주는 설정들.

```sh
"defaultProfile": "{61c54bbd-c2c6-5271-96e7-009a87ff44bf}" // 기본 프로필, GUID를 사용한다.
"theme": "system" // 테마, system, dark, light 세 가지를 사용할 수 있다.
"confirmCloseAllTabs": true // 모든 탭 닫기 시 팝업 확인 출력, true이면 팝업이 뜬다.
"startOnUserLogin": false // 컴퓨터 시작 시 터미널 실행.
"showTabsInTitlebar": true // 제목 표시줄 출력 여부.
"copyOnSelect": false // 생성 시 선택한 내용이 클립보드에 즉시 복사. 마우스 우클릭 시 붙여넣기
"copyFormatting": false // 복사 시 텍스트의 색 및 글꼴 서식도 복사된다.
"snapToGridOnResize": true // 창 크기 조절 시 가까운 문자 경계에 맞춰짐.
```

# [프로필 설정](https://docs.microsoft.com/ko-kr/windows/terminal/customize-settings/profile-settings)

* 각각의 고유한 프로필에 영향을 주는 설정들.
* 모든 프로필에 적용하고 싶은 설정들은 `defaults` 섹션에 추가하자.

```sh
"guid": "{61c54bbd-c2c6-5271-96e7-009a87ff44bf}" // 필수
"commandline": "powershell.exe" // 실행 파일
"startingDirectory": "%USERPROFILE%" // 셸이 시작하는 폴더 주소

"name": "Windows PowerShell" // 탭에 표시되는 이름
"hidden": false // 프로필 목록에 표시할 지의 여부

"suppressApplicationTitle": false // 탭 제목 자동 변경을 방지해준다. 현재 제목이 바뀌는 프로필은 WSL(Windows Subsystem for Linux)이 유일함.

"fontFace": "Cascadia Mono" // 글꼴 설정. 자세한 내용은 [여기](https://docs.microsoft.com/ko-kr/windows/terminal/cascadia-code)
"fontWeight": "normal" // 글꼴 두께

"colorScheme": "Campbell" // 프로필의 색 구성표. `scheme` 개체에 정의된다. 자세한 내용은 [여기](https://docs.microsoft.com/ko-kr/windows/terminal/customize-settings/color-schemes)
"foreground": "#rgb" // 프로필의 테마 중 글 색을 지정
"background": "#rgb" // 프로필의 테마 중 배경 색을 지정

"useAcrylic": false // 아크릴 배경 사용 여부
"arcylicOpacity": 0.5 // 아크릴 배경 투명도. `useArcylic`이 true일 때만 사용

"backgroundImage": "folder path" // 배경에 이미지 적용. `jpg, png, gif` 사용가능
"backgroundImageStretchMode": "uniformToFill" // 이미지 크기 조절. `none, uniform, fill, uniformToFill` 을 사용할 수 있다.
"backgroundImageAlignment": "center" // 배경 이미지를 창의 경계에 맞추고 싶을 때 사용한다.
"backgroundImageOpacity": 1.0 // 배경 이미지의 투명도를 조절한다.

"scrollbarState": "visible" // 스크롤 막대의 표시 유형. `visible, hidden` 두 가지 값을 사용할 수 있다.

"closeOnExit": "graceful" // 프로필 종료 또는 시작 실패에 반응하는 방법 설정. `graceful`은 exit가 입력되거나 프로세스가 정상종료될 때 프로필을 닫는다.
                          // `graceful, always, never` 값을 사용할 수 있다.
```

# [커스텀 액션 설정](https://docs.microsoft.com/ko-kr/windows/terminal/customize-settings/actions)

* 키 바인딩으로 원하는 동작을 실행시킬 수 있다.
* `command`는 등록되어 있는 키값만 사용가능
* `keys` 의 값은 `ctrl+, shift+, alt+` 세 개의 모디파이어와 키보드에 대응되는 키의 조합으로 이루어진다.

```sh
{ "command": "closeWindow", "keys": "alt+f4" } // 프로그램 닫기
{ "command": "find", "keys": "ctrl+shift+f" } // 문자열 찾기
{ "command": "openNewTabDropdown", "keys": "ctrl+shift+space" } // 드롭박스 열기
{ "command": "openSettings", "keys": "ctrl+," } // 세팅값 열기
{ "command": "toggleFullscreen", "keys": "alt+enter" } // 전체 창모드, `f11`도 된다.

{ "command": { "action": "newTab", "index": 0 }, "keys": "ctrl+shift+1" } // 새 탭. 인덱스 따라 커맨드가 달라진다.
{ "command": "duplicateTab", "keys": "ctrl+shift+d" } // 현재 탭을 새로 연다.
{ "command": "nextTab", "keys": "ctrl+tab" } // 포커스를 다음 탭으로 이동한다.
{ "command": "prevTab", "keys": "ctrl+shift+tab" } // 포커스를 이전 탭으로 이동한다.

// 창을 생성한다. `alt+shift+-`는 하단에, `alt+shift+plus`는 우측에 생성한다. (default.json)
{ "command": { "action": "splitPane", "split": "auto", "splitMode": "duplicate" }, "keys": "alt+shift+d" }, // 포커스가 있는 창의 프로필을 복제한다.
{ "command": { "action": "splitPane", "split": "vertical" }, "keys": "alt+shift+plus" },
{ "command": { "action": "splitPane", "split": "horizontal" }, "keys": "alt+shift+-" },
{ "command": { "action": "splitPane", "split": "auto" }, "keys": "alt+shift+|" }

// 창 또는 탭 생성 시 옵션
{ "command": { "action": "splitPane", "split": "vertical", "profile": "profile1" }, "keys": "ctrl+..." },
{ "command": { "action": "splitPane", "split": "vertical", "profile": "{00000000-0000-0000-0000-000000000000}" }, "keys": "ctrl+..." },
{ "command": { "action": "newTab", "index": 0 }, "keys": "ctrl+numpad_0" }

{ "command": "closePane", "keys": "ctrl+shift+w" } // 분할된 창을 하나 닫는다. 분할되지 않았을 경우 탭을 닫는다. 탭이 하나면 종료한다.
{ "command": { "action": "moveFocus", "direction": "down" }, "keys": "alt+down" } // 창의 포커스를 이동한다. 상, 하, 좌, 우 네방향으로 변경 가능하다.
{ "command": { "action": "resizePane", "direction": "down" }, "keys": "alt+shift+down" } // 창의 크기를 변경한다.


{ "command": { "action": "copy", "singleLine": false }, "keys": "ctrl+c" }, // 클립보드에 선택된 컨텐츠를 복사한다. `ctrl+shift+c, ctrl+insert`도 된다. (default.json)
{ "command": "paste", "keys": "ctrl+v" }, // 클립보드의 컨텐츠를 붙여넣는다. `ctrl+shift+v, shift+insert`도 된다. (default.json)

{ "command": "scrollUp", "keys": "ctrl+shift+up" } // 위로 한줄 스크롤. 아래도 있음
{ "command": "scrollUpPage", "keys": "ctrl+shift+pgup" } // 위로 페이지 단위 스크롤. 아래도 있음

// 폰트 사이즈를 변경한다.
{ "command": { "action": "adjustFontSize", "delta": 1 }, "keys": "ctrl+=" },
{ "command": { "action": "adjustFontSize", "delta": -1 }, "keys": "ctrl+-" }
{ "command": "resetFontSize", "keys": "ctrl+0" } // 리셋
```

# [커맨드 라인 파라미터](https://docs.microsoft.com/ko-kr/windows/terminal/command-line-arguments?tabs=windows)

* `Windows Terminal` 의 새 인스턴스를 열 때 사용할 수 있는 명령어들
* 기본 모양은 `wt [options] [command ; ]` 이다.
* `WT`와 `powershell` 의 명령줄 구분 기호가 세미콜론으로 동일하기 때문에 문자열을 작은 따옴표로 래핑하던가, 세미콜론을 이스케이프 하거나, `--%` 를 사용하여 나머지 부분을 인수로 처리하도록 한다.

```sh
// "Ubuntu-18.04" 프로필 인스턴스 열기
wt -p "Ubuntu-18.04"   // cmd, powershell
cmd.exe /c "wt.exe" -p "Ubuntu-18.04"    // linux

// 시작 디렉터리가 d드라이브인 인스턴스 열기
wt -d d:\    // cmd, powershell
cmd.exe /c "wt.exe" -d d:\    // linux

// 탭이 두 개 있는 새 인스턴스 열기
wt ; ;    // cmd
wt `; `;    // powershell
cmd.exe /c "wt.exe" \; \;    // linux

// `cmd` 와 `powershell`을 탭으로 갖는 인스턴스 열기
wt -p "Command Prompt" ; new-tab -p "Windows PowerShell"    // cmd
wt -p "Command Prompt" `; new-tab -p "Windows PowerShell"    // powershell
cmd.exe /c "wt.exe" -p "Command Prompt" \; new-tab -p "Windows Powershell"    // linux

// 하나의 탭에 `cmd`, `powershell`, `linux` 3개의 창이 떠있는 인스턴스 열기
wt -p "Command Prompt" ; split-pane -p "Windows PowerShell" ; split-pane -H wsl.exe    // cmd
wt -p "Command Prompt" `; split-pane -p "Windows PowerShell" `; split-pane -H wsl.exe    // powershell
cmd.exe /c "wt.exe" -p "Command Prompt" \; split-pane -p "Windows PowerShell" \; split-pane -H wsl.exe    // linux
```

# [커맨드 라인 팔레트](https://docs.microsoft.com/ko-kr/windows/terminal/command-palette)

* 현재 인스턴스에서 파라미터를 이용한 명령어를 사용하고 싶을 때 사용
* 등록되어 있는 커맨드들을 검색하여 실행시킬 수도 있다.

# 코드

* 미리보기에서 절대경로는 처리가 안되나..?

[settings.json](file:///C:/Users/Kanghyuk/AppData/Local/Packages/Microsoft.WindowsTerminal_8wekyb3d8bbwe/LocalState/settings.json)

<a href="file:///C:/Users/Kanghyuk/AppData/Local/Packages/Microsoft.WindowsTerminal_8wekyb3d8bbwe/LocalState/settings.json"> `settings.json` </a>

* default.json

```sh
// THIS IS AN AUTO-GENERATED FILE! Changes to this file will be ignored.
{
    "defaultProfile": "{61c54bbd-c2c6-5271-96e7-009a87ff44bf}",

    // Launch Settings
    "initialCols": 120,
    "initialRows": 30,
    "launchMode": "default",
    "alwaysOnTop": false,

    // Selection
    "copyOnSelect": false,
    "copyFormatting": true,
    "wordDelimiters": " /\\()\"'-.,:;<>~!@#$%^&*|+=[]{}~?\u2502",

    // Tab UI
    "alwaysShowTabs": true,
    "showTabsInTitlebar": true,
    "showTerminalTitleInTitlebar": true,
    "tabWidthMode": "equal",
    "useTabSwitcher": true,

    // Miscellaneous
    "confirmCloseAllTabs": true,
    "startOnUserLogin":  false,
    "theme": "system",
    "snapToGridOnResize": true,

    "profiles":
    [
        {
            "guid": "{61c54bbd-c2c6-5271-96e7-009a87ff44bf}",
            "name": "Windows PowerShell",
            "commandline": "%SystemRoot%\\System32\\WindowsPowerShell\\v1.0\\powershell.exe",
            "icon": "ms-appx:///ProfileIcons/{61c54bbd-c2c6-5271-96e7-009a87ff44bf}.png",
            "colorScheme": "Campbell",
            "antialiasingMode": "grayscale",
            "closeOnExit": "graceful",
            "cursorShape": "bar",
            "fontFace": "Cascadia Mono",
            "fontSize": 12,
            "hidden": false,
            "historySize": 9001,
            "padding": "8, 8, 8, 8",
            "snapOnInput": true,
            "altGrAliasing": true,
            "startingDirectory": "%USERPROFILE%",
            "useAcrylic": false
        },
        {
            "guid": "{0caa0dad-35be-5f56-a8ff-afceeeaa6101}",
            "name": "Command Prompt",
            "commandline": "%SystemRoot%\\System32\\cmd.exe",
            "icon": "ms-appx:///ProfileIcons/{0caa0dad-35be-5f56-a8ff-afceeeaa6101}.png",
            "colorScheme": "Campbell",
            "antialiasingMode": "grayscale",
            "closeOnExit": "graceful",
            "cursorShape": "bar",
            "fontFace": "Cascadia Mono",
            "fontSize": 12,
            "hidden": false,
            "historySize": 9001,
            "padding": "8, 8, 8, 8",
            "snapOnInput": true,
            "altGrAliasing": true,
            "startingDirectory": "%USERPROFILE%",
            "useAcrylic": false
        }
    ],
    "schemes":
    [
        // A profile can override the following color scheme values:
        //   - "foreground"
        //   - "background"
        //   - "cursorColor"
        {
            "name": "Campbell",
            "foreground": "#CCCCCC",
            "background": "#0C0C0C",
            "cursorColor": "#FFFFFF",
            "black": "#0C0C0C",
            "red": "#C50F1F",
            "green": "#13A10E",
            "yellow": "#C19C00",
            "blue": "#0037DA",
            "purple": "#881798",
            "cyan": "#3A96DD",
            "white": "#CCCCCC",
            "brightBlack": "#767676",
            "brightRed": "#E74856",
            "brightGreen": "#16C60C",
            "brightYellow": "#F9F1A5",
            "brightBlue": "#3B78FF",
            "brightPurple": "#B4009E",
            "brightCyan": "#61D6D6",
            "brightWhite": "#F2F2F2"
        },
        {
            "name": "Campbell Powershell",
            "foreground": "#CCCCCC",
            "background": "#012456",
            "cursorColor": "#FFFFFF",
            "black": "#0C0C0C",
            "red": "#C50F1F",
            "green": "#13A10E",
            "yellow": "#C19C00",
            "blue": "#0037DA",
            "purple": "#881798",
            "cyan": "#3A96DD",
            "white": "#CCCCCC",
            "brightBlack": "#767676",
            "brightRed": "#E74856",
            "brightGreen": "#16C60C",
            "brightYellow": "#F9F1A5",
            "brightBlue": "#3B78FF",
            "brightPurple": "#B4009E",
            "brightCyan": "#61D6D6",
            "brightWhite": "#F2F2F2"
        },
        {
            "name": "Vintage",
            "foreground": "#C0C0C0",
            "background": "#000000",
            "cursorColor": "#FFFFFF",
            "black": "#000000",
            "red": "#800000",
            "green": "#008000",
            "yellow": "#808000",
            "blue": "#000080",
            "purple": "#800080",
            "cyan": "#008080",
            "white": "#C0C0C0",
            "brightBlack": "#808080",
            "brightRed": "#FF0000",
            "brightGreen": "#00FF00",
            "brightYellow": "#FFFF00",
            "brightBlue": "#0000FF",
            "brightPurple": "#FF00FF",
            "brightCyan": "#00FFFF",
            "brightWhite": "#FFFFFF"
        },
        {
            "name": "One Half Dark",
            "foreground": "#DCDFE4",
            "background": "#282C34",
            "cursorColor": "#FFFFFF",
            "black": "#282C34",
            "red": "#E06C75",
            "green": "#98C379",
            "yellow": "#E5C07B",
            "blue": "#61AFEF",
            "purple": "#C678DD",
            "cyan": "#56B6C2",
            "white": "#DCDFE4",
            "brightBlack": "#5A6374",
            "brightRed": "#E06C75",
            "brightGreen": "#98C379",
            "brightYellow": "#E5C07B",
            "brightBlue": "#61AFEF",
            "brightPurple": "#C678DD",
            "brightCyan": "#56B6C2",
            "brightWhite": "#DCDFE4"
        },
        {
            "name": "One Half Light",
            "foreground": "#383A42",
            "background": "#FAFAFA",
            "cursorColor": "#4F525D",
            "black": "#383A42",
            "red": "#E45649",
            "green": "#50A14F",
            "yellow": "#C18301",
            "blue": "#0184BC",
            "purple": "#A626A4",
            "cyan": "#0997B3",
            "white": "#FAFAFA",
            "brightBlack": "#4F525D",
            "brightRed": "#DF6C75",
            "brightGreen": "#98C379",
            "brightYellow": "#E4C07A",
            "brightBlue": "#61AFEF",
            "brightPurple": "#C577DD",
            "brightCyan": "#56B5C1",
            "brightWhite": "#FFFFFF"
        },
        {
            "name": "Solarized Dark",
            "foreground": "#839496",
            "background": "#002B36",
            "cursorColor": "#FFFFFF",
            "black": "#002B36",
            "red": "#DC322F",
            "green": "#859900",
            "yellow": "#B58900",
            "blue": "#268BD2",
            "purple": "#D33682",
            "cyan": "#2AA198",
            "white": "#EEE8D5",
            "brightBlack": "#073642",
            "brightRed": "#CB4B16",
            "brightGreen": "#586E75",
            "brightYellow": "#657B83",
            "brightBlue": "#839496",
            "brightPurple": "#6C71C4",
            "brightCyan": "#93A1A1",
            "brightWhite": "#FDF6E3"
        },
        {
            "name": "Solarized Light",
            "foreground": "#657B83",
            "background": "#FDF6E3",
            "cursorColor": "#002B36",
            "black": "#002B36",
            "red": "#DC322F",
            "green": "#859900",
            "yellow": "#B58900",
            "blue": "#268BD2",
            "purple": "#D33682",
            "cyan": "#2AA198",
            "white": "#EEE8D5",
            "brightBlack": "#073642",
            "brightRed": "#CB4B16",
            "brightGreen": "#586E75",
            "brightYellow": "#657B83",
            "brightBlue": "#839496",
            "brightPurple": "#6C71C4",
            "brightCyan": "#93A1A1",
            "brightWhite": "#FDF6E3"
        },
        {
            "name": "Tango Dark",
            "foreground": "#D3D7CF",
            "background": "#000000",
            "cursorColor": "#FFFFFF",
            "black": "#000000",
            "red": "#CC0000",
            "green": "#4E9A06",
            "yellow": "#C4A000",
            "blue": "#3465A4",
            "purple": "#75507B",
            "cyan": "#06989A",
            "white": "#D3D7CF",
            "brightBlack": "#555753",
            "brightRed": "#EF2929",
            "brightGreen": "#8AE234",
            "brightYellow": "#FCE94F",
            "brightBlue": "#729FCF",
            "brightPurple": "#AD7FA8",
            "brightCyan": "#34E2E2",
            "brightWhite": "#EEEEEC"
        },
        {
            "name": "Tango Light",
            "foreground": "#555753",
            "background": "#FFFFFF",
            "cursorColor": "#000000",
            "black": "#000000",
            "red": "#CC0000",
            "green": "#4E9A06",
            "yellow": "#C4A000",
            "blue": "#3465A4",
            "purple": "#75507B",
            "cyan": "#06989A",
            "white": "#D3D7CF",
            "brightBlack": "#555753",
            "brightRed": "#EF2929",
            "brightGreen": "#8AE234",
            "brightYellow": "#FCE94F",
            "brightBlue": "#729FCF",
            "brightPurple": "#AD7FA8",
            "brightCyan": "#34E2E2",
            "brightWhite": "#EEEEEC"
        }
    ],
    "actions":
    [
        // Application-level Keys
        { "command": "closeWindow", "keys": "alt+f4" },
        { "command": "toggleFullscreen", "keys": "alt+enter" },
        { "command": "toggleFullscreen", "keys": "f11" },
        { "command": "toggleFocusMode" },
        { "command": "toggleAlwaysOnTop" },
        { "command": "openNewTabDropdown", "keys": "ctrl+shift+space" },
        { "command": "openSettings", "keys": "ctrl+," },
        { "command": { "action": "openSettings", "target": "defaultsFile" }, "keys": "ctrl+alt+," },
        { "command": "find", "keys": "ctrl+shift+f" },
        { "command": "toggleRetroEffect" },
        { "command": "openTabColorPicker" },
        { "command": "commandPalette", "keys":"ctrl+shift+p" },

        // Tab Management
        // "command": "closeTab" is unbound by default.
        //   The closeTab command closes a tab without confirmation, even if it has multiple panes.
        { "command": "closeOtherTabs" },
        { "command": "closeTabsAfter" },
        { "command": "newTab", "keys": "ctrl+shift+t" },
        { "command": { "action": "newTab", "index": 0 }, "keys": "ctrl+shift+1" },
        { "command": { "action": "newTab", "index": 1 }, "keys": "ctrl+shift+2" },
        { "command": { "action": "newTab", "index": 2 }, "keys": "ctrl+shift+3" },
        { "command": { "action": "newTab", "index": 3 }, "keys": "ctrl+shift+4" },
        { "command": { "action": "newTab", "index": 4 }, "keys": "ctrl+shift+5" },
        { "command": { "action": "newTab", "index": 5 }, "keys": "ctrl+shift+6" },
        { "command": { "action": "newTab", "index": 6 }, "keys": "ctrl+shift+7" },
        { "command": { "action": "newTab", "index": 7 }, "keys": "ctrl+shift+8" },
        { "command": { "action": "newTab", "index": 8 }, "keys": "ctrl+shift+9" },
        { "command": "duplicateTab", "keys": "ctrl+shift+d" },
        { "command": "nextTab", "keys": "ctrl+tab" },
        { "command": "prevTab", "keys": "ctrl+shift+tab" },
        { "command": { "action": "switchToTab", "index": 0 }, "keys": "ctrl+alt+1" },
        { "command": { "action": "switchToTab", "index": 1 }, "keys": "ctrl+alt+2" },
        { "command": { "action": "switchToTab", "index": 2 }, "keys": "ctrl+alt+3" },
        { "command": { "action": "switchToTab", "index": 3 }, "keys": "ctrl+alt+4" },
        { "command": { "action": "switchToTab", "index": 4 }, "keys": "ctrl+alt+5" },
        { "command": { "action": "switchToTab", "index": 5 }, "keys": "ctrl+alt+6" },
        { "command": { "action": "switchToTab", "index": 6 }, "keys": "ctrl+alt+7" },
        { "command": { "action": "switchToTab", "index": 7 }, "keys": "ctrl+alt+8" },
        { "command": { "action": "switchToTab", "index": 8 }, "keys": "ctrl+alt+9" },

        // Pane Management
        { "command": "closePane", "keys": "ctrl+shift+w" },
        { "command": { "action": "splitPane", "split": "horizontal" }, "keys": "alt+shift+-" },
        { "command": { "action": "splitPane", "split": "vertical" }, "keys": "alt+shift+plus" },
        { "command": { "action": "resizePane", "direction": "down" }, "keys": "alt+shift+down" },
        { "command": { "action": "resizePane", "direction": "left" }, "keys": "alt+shift+left" },
        { "command": { "action": "resizePane", "direction": "right" }, "keys": "alt+shift+right" },
        { "command": { "action": "resizePane", "direction": "up" }, "keys": "alt+shift+up" },
        { "command": { "action": "moveFocus", "direction": "down" }, "keys": "alt+down" },
        { "command": { "action": "moveFocus", "direction": "left" }, "keys": "alt+left" },
        { "command": { "action": "moveFocus", "direction": "right" }, "keys": "alt+right" },
        { "command": { "action": "moveFocus", "direction": "up" }, "keys": "alt+up" },

        // Clipboard Integration
        { "command": { "action": "copy", "singleLine": false }, "keys": "ctrl+shift+c" },
        { "command": { "action": "copy", "singleLine": false }, "keys": "ctrl+insert" },
        { "command": "paste", "keys": "ctrl+shift+v" },
        { "command": "paste", "keys": "shift+insert" },

        // Scrollback
        { "command": "scrollDown", "keys": "ctrl+shift+down" },
        { "command": "scrollDownPage", "keys": "ctrl+shift+pgdn" },
        { "command": "scrollUp", "keys": "ctrl+shift+up" },
        { "command": "scrollUpPage", "keys": "ctrl+shift+pgup" },

        // Visual Adjustments
        { "command": { "action": "adjustFontSize", "delta": 1 }, "keys": "ctrl+=" },
        { "command": { "action": "adjustFontSize", "delta": -1 }, "keys": "ctrl+-" },
        { "command": "resetFontSize", "keys": "ctrl+0" },

        // Other commands
        {
            // Select color scheme...
            "name": { "key": "SetColorSchemeParentCommandName" },
            "commands": [
                {
                    "iterateOn": "schemes",
                    "name": "${scheme.name}",
                    "command": { "action": "setColorScheme", "colorScheme": "${scheme.name}" }
                }
            ]
        },
        {
            // New tab...
            "name": { "key": "NewTabParentCommandName" },
            "commands": [
                {
                    "iterateOn": "profiles",
                    "icon": "${profile.icon}",
                    "name": "${profile.name}",
                    "command": { "action": "newTab", "profile": "${profile.name}" }
                }
            ]
        },
        {
            // Split pane...
            "name": { "key": "SplitPaneParentCommandName" },
            "commands": [
                {
                    "iterateOn": "profiles",
                    "icon": "${profile.icon}",
                    "name": "${profile.name}...",
                    "commands": [
                        {
                            "command": { "action": "splitPane", "profile": "${profile.name}", "split": "auto" }
                        },
                        {
                            "command": { "action": "splitPane", "profile": "${profile.name}", "split": "vertical" }
                        },
                        {
                            "command": { "action": "splitPane", "profile": "${profile.name}", "split": "horizontal" }
                        }
                    ]
                }
            ]
        }
    ]
}

```