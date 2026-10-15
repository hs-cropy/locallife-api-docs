# Cropy API 문서

AI 기반 농작물 병해충 진단 서비스 **Cropy**의 백엔드 API 명세를 공유하는 저장소입니다.

**문서 접속: [Cropy API 문서 열기](https://hs-cropy.github.io/locallife-api-docs/api-docs.html)**

별도의 설치나 백엔드 실행 없이 브라우저에서 API 설명, 요청 파라미터, 응답 형식과 오류 코드를 확인할 수 있습니다.

## 제공 파일

| 파일 | 용도 |
| --- | --- |
| [API 문서 HTML](https://hs-cropy.github.io/locallife-api-docs/api-docs.html) | ReDoc으로 렌더링한 API 문서 |
| [OpenAPI JSON](https://hs-cropy.github.io/locallife-api-docs/api-docs.json) | Swagger Editor 등에서 가져올 수 있는 OpenAPI 3.1.0 명세 |

이 사이트는 정적 문서를 제공합니다. 실제 진단 요청이나 이력 조회를 실행하려면 별도로 실행 중인 Cropy 백엔드가 필요합니다.

## API 구성

업무 API는 총 12개이며, 공통 경로는 `/api/v1`입니다.

| 그룹 | API 수 | 주요 기능 |
| --- | ---: | --- |
| `health` | 3 | 서버 생존 확인, 모델 준비 상태, 지원 기능·업로드 한도 조회 |
| `diagnosis` | 5 | 사진 진단, 재촬영, 저장 복구, 이력 목록·상세 조회 |
| `diseases` | 2 | 병해 정보 목록·상세 조회 |
| `offline` | 2 | 브라우저 모델 묶음 조회, 기기 진단 기록 동기화 |

## 저장소 구조

```text
locallife-api-docs/
├── README.md
└── docs/
    ├── api-docs.html   # API 문서 화면
    ├── api-docs.json   # OpenAPI 명세
    ├── index.html     # 기본 주소에서 api-docs.html로 연결
    └── .nojekyll      # Jekyll 처리 없이 정적 파일 제공
```

## 배포

GitHub Pages는 `main` 브랜치의 `/docs` 폴더를 게시합니다.

팀원에게 공유할 주소:

```text
https://hs-cropy.github.io/locallife-api-docs/api-docs.html
```

## 문서 갱신

문서 원본은 [Cropy 백엔드 저장소](https://github.com/hs-cropy/Cropy)에서 관리합니다. 백엔드 코드 변경 사항이 이 저장소에 자동으로 반영되지는 않습니다.

1. Cropy 백엔드 변경 사항을 반영해 OpenAPI JSON과 문서 HTML을 다시 생성합니다.
2. 생성된 `docs/api/openapi.json`을 이 저장소의 `docs/api-docs.json`으로 복사합니다.
3. 생성된 `docs/api/openapi.html`을 이 저장소의 `docs/api-docs.html`로 복사합니다.
4. 변경 내용을 확인한 뒤 `main` 브랜치에 커밋·푸시합니다.
5. GitHub Pages 배포 완료 후 위 문서 주소에서 변경 내용을 확인합니다.

HTML에는 명세가 내장되어 있으므로 **JSON과 HTML을 함께 갱신**해야 합니다. `.nojekyll`과 `index.html`은 유지합니다.
