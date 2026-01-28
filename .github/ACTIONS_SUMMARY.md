# GitHub Actions 설정 및 상태 정리

이 문서는 `.github` 디렉토리 내의 GitHub Actions 워크플로우 파일들에 대한 설명과 현재 활성화/비활성화 상태를 정리한 것입니다.

## ✅ 활성화된 항목 (코드 오류 검사)
이 항목들은 코드가 수정(push/PR)될 때마다 자동으로 실행되어 코드 스타일과 잠재적인 오류를 검사합니다.

| 파일명 | 설명 | 상태 |
|---|---|---|
| `workflows/format-backend.yaml` | **백엔드(Python)** 코드의 스타일을 검사하고 형식을 맞춥니다. | **Enabled** |
| `workflows/format-build-frontend.yaml` | **프론트엔드(Node.js)** 코드의 스타일을 검사하고 빌드 테스트를 수행합니다. | **Enabled** |

## ❌ 비활성화된 항목 (배포 및 자동화)
개인 개발 환경이나 로컬 테스트 목적에는 불필요하거나 리소스를 많이 소모하는 작업들입니다. `.disabled` 확장자가 붙어 있어 실행되지 않습니다.

| 원본 파일명 | 설명 | 상태 |
|---|---|---|
| `workflows/docker-build.yaml` | Docker 이미지를 빌드하여 GitHub Container Registry에 업로드합니다. (실행 시간이 깁니다) | **Disabled** |
| `workflows/build-release.yml` | 버전 태그가 달릴 때 GitHub Release를 생성합니다. | **Disabled** |
| `workflows/deploy-to-hf-spaces.yml` | Hugging Face Spaces에 자동으로 배포합니다. | **Disabled** |
| `workflows/release-pypi.yml` | Python 패키지 저장소(PyPI)에 라이브러리를 배포합니다. | **Disabled** |
| `dependabot.yml` | 의존성 라이브러리의 새 버전이 나오면 업데이트 PR을 자동으로 생성합니다. | **Disabled** |

## ℹ️ 기타 파일
*   `workflows/*.disabled`: 이전에 이미 비활성화되어 있던 다른 테스트 파일들입니다. (`codespell`, `integration-test`, `lint-backend` 등)

---
> **참고**: 비활성화된 기능을 다시 사용하려면 파일 이름에서 `.disabled`를 제거하면 됩니다.
