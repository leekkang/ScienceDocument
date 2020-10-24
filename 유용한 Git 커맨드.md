# Git Commands

* 전역 텍스트 편집기를 `VSCode` 로 지정 + 커맨드라인이 편집기가 닫힐때까지 대기
  * `.gitconfig` 파일은 `$HOME` 경로에 있다.

```git
git config --global core.editor "code --wait"
git config --global -e // 편집기로 .gitconfig 열기
```