# 다른 PC에 `/parksplan` 설치하기

저장소: https://github.com/blueskynnn-cloud/claude-commands

## 🆕 새 PC 최초 설치 (1회만)

### 옵션 A: 읽기 전용 (간단, 인증 불필요)

Git Bash에서:

```bash
# 기존 ~/.claude/commands 폴더가 있다면 백업
[ -d ~/.claude/commands ] && mv ~/.claude/commands ~/.claude/commands.bak

# 저장소 clone
git clone https://github.com/blueskynnn-cloud/claude-commands.git ~/.claude/commands

# 확인
ls ~/.claude/commands
```

Claude Code 재시작하면 `/parksplan` 자동 인식.

### 옵션 B: 쓰기 권한 (해당 PC에서도 커맨드 수정·push 하려면)

```bash
# GitHub CLI 설치 (없으면)
winget install --id GitHub.cli --accept-source-agreements --accept-package-agreements

# 새 터미널 열고 로그인
gh auth login
# → GitHub.com / HTTPS / Login with a web browser 선택

# 기존 commands 백업 후 clone
[ -d ~/.claude/commands ] && mv ~/.claude/commands ~/.claude/commands.bak
git clone https://github.com/blueskynnn-cloud/claude-commands.git ~/.claude/commands
```

## 🔄 기존 PC에서 최신 반영 (수시)

```bash
cd ~/.claude/commands && git pull
```

## ✍️ 커맨드 수정 후 다른 PC와 공유

수정한 PC에서:
```bash
cd ~/.claude/commands
git add .
git commit -m "update parksplan"
git push
```

다른 PC에서:
```bash
cd ~/.claude/commands && git pull
```

## 💡 팁

- **새 커맨드 추가:** `~/.claude/commands/` 에 `커맨드명.md` 파일만 만들면 `/커맨드명` 으로 자동 인식됨
- **자동 pull:** PowerShell 프로필이나 bash `.bashrc`에 `cd ~/.claude/commands && git pull 2>/dev/null; cd -` 추가하면 터미널 열 때마다 동기화
- **충돌 나면:** `git stash && git pull && git stash pop` 으로 로컬 변경 유지한 채 동기화
