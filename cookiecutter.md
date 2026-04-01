# 쿠키커터

## 소개

[Cookiecutter](https://github.com/cookiecutter/cookiecutter)는 템플릿을 사용하여 프로젝트를 생성하는 명령줄 유틸리티입니다. 미리 정의된 파일과 디렉터리를 포함하는 프로젝트 구조 생성을 자동화하여 일관성을 유지하고 새 프로젝트를 시작할 때 시간을 절약해 줍니다. 이 도구는 여러 프로젝트에서 표준화된 설정을 유지하려는 개발자에게 특히 유용합니다.

**Python 패키지 템플릿 예:** [opengeos/cookiecutter-pypackage](https://github.com/opengeos/cookiecutter-pypackage)

## 용법

이 가이드는 파이썬 패키지 생성, 배포 구성, 버전 관리 및 릴리스 관리에 대한 단계별 안내를 제공합니다. 이 지침을 따르면 워크플로를 간소화할 수 있습니다.

## 필수 조건

진행하기 전에 pip 또는 conda를 사용하여 필요한 도구를 설치하십시오.

### pip 사용

```bash
pip install cookiecutter bump-my-version
```

### conda를 사용하세요

```bash
conda install -c conda-forge cookiecutter bump-my-version
```

## 단계별 지침

### 1. 패키지 구조 생성

Cookiecutter를 사용하여 Python 패키지의 초기 구조를 만드세요. 이 명령은 템플릿 저장소를 복제하고 필요한 파일과 디렉터리를 설정합니다. 안내에 따라 패키지를 사용자 지정하세요.

```bash
cookiecutter gh:opengeos/cookiecutter-pypackage
```

### 2. GitHub에 저장소 생성

1. [GitHub](https://github.com)에 접속하여 새롭고 비어 있는 저장소를 생성하세요. 저장소 이름은 패키지 이름과 동일하게 지정하세요.
2. README, 라이선스 또는 .gitignore 파일로 초기화하지 마십시오.

### 3. GitHub Actions 권한 구성

GitHub Actions에서 저장소에 대한 읽기 및 쓰기 작업을 수행할 수 있도록 설정하세요.

1. GitHub에서 저장소로 이동합니다.
2. `설정` > `작업` > `일반` > `워크플로 권한`으로 이동합니다.
3. **읽기 및 쓰기 작업**을 허용하도록 설정을 조정하십시오.

### 4. 저장소 복제

새로 생성된 GitHub 저장소를 로컬 컴퓨터에 복제하세요.

```bash
git clone [저장소 URL]
```

### 5. 쿠키커터 템플릿에서 파일 복사

Cookiecutter 템플릿에서 생성된 파일을 복제한 저장소에 복사하세요.

### 6. 변경 사항 커밋 및 푸시

변경 사항을 커밋하고 GitHub 저장소에 푸시하세요.

```bash
git add .
git commit -m "최초 커밋"
git push origin main
```

### 7. PyPI API 토큰 생성

1. [pypi.org](https://pypi.org)에 접속하여 로그인하거나 계정을 생성하세요.
2. `계정 설정` > `API 토큰`으로 이동합니다.
3. '계정 전체' 범위로 새 API 토큰을 생성합니다. 나중에 사용할 수 있도록 토큰을 복사합니다.

### 8. PyPI 자격 증명을 GitHub Secrets에 추가

PyPI 자격 증명을 GitHub 저장소에 안전하게 저장하세요.

1. GitHub에서 저장소로 이동합니다.
2. `설정` > `비밀` > `새 저장소 비밀`로 이동합니다.
3. 다음 비밀들을 추가하세요:

- `PYPI_USERNAME`: 값으로 `__token__`을 사용하세요.
- `PYPI_PASSWORD`: 이전에 복사한 API 토큰을 사용하세요.

### 9. GitHub 릴리스 생성

GitHub에서 릴리스를 생성하여 패키지 배포를 시작하세요.

1. GitHub 저장소의 `릴리스` 섹션으로 이동합니다.
2. '새 릴리스 초안 작성'을 클릭합니다.
3. 안내에 따라 릴리스를 생성하세요.

### 10. GitHub Pages 활성화

문서 또는 기타 정적 콘텐츠를 호스팅하려면 GitHub Pages를 활성화하세요.

1. '설정' > '페이지'로 이동합니다.
2. 소스로 `gh-pages` 브랜치를 선택합니다.
3. '저장'을 클릭하세요.

### 11. bump-my-version을 사용하여 버전 관리

`bump-my-version` 명령어를 사용하여 패키지의 버전 업데이트를 처리하세요.

1. 변경 사항을 미리 보기 위해 예행연습을 수행하십시오.

```bash
버전 업데이트 [패치/마이너/메이저] --드라이런 --상세 정보 표시
```

2. 버전 업데이트를 적용합니다.

```bash
버전 업데이트 [패치/마이너/메이저]
```

### 12. 버전 태그 및 변경 사항 푸시

버전을 업데이트한 후 변경 사항과 태그를 GitHub에 푸시하세요.

```bash
git push --tags
git push
```

### 13. 새 GitHub 릴리스 생성

마지막으로, 업데이트된 버전을 반영하여 GitHub에 새 릴리스를 생성합니다.

1. **9단계**에 설명된 과정을 반복합니다.

## 결론

이 가이드를 따르면 Cookiecutter 및 관련 도구를 사용하여 Python 패키지를 효율적으로 설정, 구성 및 관리할 수 있습니다. 이 워크플로는 일관성을 보장하고, 반복적인 작업을 자동화하며, 패키지 배포 프로세스를 간소화합니다.

자세한 내용은 [Cookiecutter](https://github.com/cookiecutter/cookiecutter) 및 [bump-my-version](https://github.com/callowayproject/bump-my-version)의 공식 문서를 참조하십시오.