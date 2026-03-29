# init-free

새 프로젝트의 초기 환경을 자동으로 셋업하는 Claude Code 플러그인.

## 개요

CLAUDE.md 생성과 `.claude/settings.local.json` 권한 설정을 한 번에 처리하여, 승인 피로 없이 바로 개발을 시작할 수 있게 해준다.

## 주요 기능

- **프로젝트 분석**: 기존 파일, 언어/프레임워크 자동 감지
- **CLAUDE.md 생성**: 프로젝트 종류에 맞는 개발 가이드 자동 작성
- **settings.local.json 생성**: 범용 개발 허용 규칙 자동 설정
- **기존 설정 병합**: 이미 settings가 있으면 덮어쓰지 않고 병합
- **안전한 기본값**: rm, kill, sudo, chmod 등 위험 명령어는 제외

## 실행 흐름

```
프로젝트 분석 → CLAUDE.md 생성 → settings.local.json 생성 → 완료 리포트
```

1. **프로젝트 분석**: 기존 파일 확인, 프로젝트 종류 판별
2. **CLAUDE.md 생성**: 빌드/테스트 명령어, 아키텍처 등 포함
3. **settings.local.json 생성**: 범용 허용 규칙 + 프로젝트별 추가 규칙
4. **완료 리포트**: 생성된 파일과 허용 항목 요약

## 지원 프로젝트 종류

| 감지 파일 | 프로젝트 종류 | 추가 허용 규칙 |
|-----------|-------------|---------------|
| `package.json` (yarn) | Node (yarn) | `Bash(yarn:*)` |
| `pnpm-lock.yaml` | Node (pnpm) | `Bash(pnpm:*)` |
| `bun.lockb` | Node (bun) | `Bash(bun:*)` |
| `pyproject.toml` | Python | `Bash(pip:*)`, `Bash(pytest:*)` |
| `Cargo.toml` | Rust | `Bash(cargo:*)` |
| `go.mod` | Go | `Bash(go:*)` |
| `docker-compose.yml` | Docker | `Bash(docker:*)` |

## 트리거 키워드

`/init-free`, `프로젝트 초기화`, `프로젝트 셋업`, `새 프로젝트 시작`, `init`, `세팅해줘`, `환경설정`, `승인피로`, `settings 만들어줘`

## 플러그인 구조

```
init-free/
├── .claude-plugin/
│   └── plugin.json
├── skills/
│   ├── SKILL.md
│   └── evals/
│       └── evals.json
└── README.md
```

## 설치

이 폴더를 Claude Code 플러그인 디렉토리에 배치하면 자동으로 인식된다.

## 작성자

tov
