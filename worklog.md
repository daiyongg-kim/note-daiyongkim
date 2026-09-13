# worklog

## 2026-09-13 — 파이썬 문법 색칠
- **요청**: "coloring 도 좀 해줘."
- **결과**: `dist/index.html` — textarea 뒤에 색칠한 `<pre>` 를 깔고 앞 글자만 투명하게(CodeMirror 없이 의존성 0). 대안 순서를 주석→문자열→키워드→숫자→내장 으로 고정해 `# def` 와 문자열 안의 단어가 안 물들게 했고, 삼중 따옴표를 홑따옴표보다 앞에 뒀다. 두 겹 정렬은 `.layer` 한 클래스로 묶고 스크롤 동기화. 브라우저에서 주석/독스트링/실행/자동 인덴트 전부 확인. 배포 완료.

## 2026-09-13 — 자동 인덴트
- **요청**: "그리고.. 웹사이트에 자동 인덴트 정도는 해줘야지."
- **결과**: Tab/Shift+Tab(블록 단위), Enter(들여쓰기 유지 · `:` 뒤 +4 · return/pass/break/continue/raise 뒤 −4), Backspace(4칸 단위), ⌘/Ctrl+Enter 실행. `document.execCommand('insertText')` 로 브라우저 실행취소 스택 보존.

## 2026-09-13 — note.daiyongkim.com 파이썬 연습장
- **요청**: "note.daiyongkim.com 에.. python 코딩 테스트 할 수 있는 걸 만들고 싶어" → "그냥 따라하기 practice 같은거야.. 빌드 gradle 설치하는건 번거러워서.." → "너가 cloudflare 들어가서 해줘."
- **결과**: Pyodide(CPython→WASM) 기반 브라우저 실행 연습장. 서버·샌드박스 불필요. GitHub Pages 배포(`dist/`, 빌드 단계 없음), Cloudflare DNS + 커스텀 도메인 + HTTPS 강제까지 완료. 
  - 함정: **워크플로 방식 Pages 배포는 `CNAME` 파일만으로 커스텀 도메인이 안 잡힌다** — `gh api -X PUT .../pages -f cname=...` 로 따로 넣어야 했다. `https_enforced` 를 같이 주면 인증서 발급 전이라 404 로 거부되므로 도메인 → 인증서 대기 → HTTPS 강제 2단계.
