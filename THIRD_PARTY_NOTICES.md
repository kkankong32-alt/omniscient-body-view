# Third-Party Notices — 전지적 몸속시점

이 앱(및 단일 실행 파일 `전지적_몸속시점_실행.html`)에 **포함되어 배포되는** 제3자 데이터·코드와,
빌드에만 쓰이고 배포물에는 들어가지 않는 도구를 구분해 적는다. 라이선스는 각 원본의 LICENSE/공식
페이지를 직접 확인한 값이다(확인 경위: `docs/10_LICENSE_VERIFICATION.md`, `docs/33_OPUS55_REBUILD_ARCHITECTURE.md`).

## 1. 배포물에 포함되는 데이터·코드

| 이름 | 버전/커밋 | 쓰는 곳 | 라이선스 | 필수 표기 |
|---|---|---|---|---|
| **BodyParts3D** (DBCLS) | Release 4.0, IS-A 전체 2,234 메시(`isa_BP3D_4.0_obj_99`) | 전신 3D 인체 모형(뼈·근육·기관·혈관·피부), 팔 움직임 실험의 실제 오른팔 뼈·근육 | **CC BY 4.0 International** | "BodyParts3D, © The Database Center for Life Science licensed under CC Attribution 4.0 International" |
| **Human Atlas** (ashemag/human-atlas) | `1c38bf3` (2026-09-06) | BodyParts3D를 브라우저용(atlas.json + gzip 청크)으로 변환한 데이터 `public/atlas/`, 파트별 GPU 상태 렌더링 방식을 vanilla JS로 다시 구현(`src/atlas/*`) | **MIT** | Copyright (c) 2026 ashemag |
| **three.js** | 0.166.x | 3D 렌더링, `OrbitControls`, `RoomEnvironment`, `BufferGeometryUtils`, `MarchingCubes`(액체·혼합물 표면), `RoundedBoxGeometry`(김밥 재료) | **MIT** | Copyright © 2010-2024 three.js authors |
| **Lucide** | 1.48.0 | 일반 UI 아이콘 일부의 SVG 경로(`src/ui/icons.js` — 필요한 아이콘만 옮김) | **ISC** | Copyright (c) for portions of Lucide are held by Cole Bemis 2013-2022 as part of Feather (MIT). All other copyright (c) for Lucide are held by Lucide Contributors 2022. |

가공 사실:
- BodyParts3D 원본 좌표·형태는 바꾸지 않았다. 앱은 파트마다 색을 새로 입히고(원본에 재질 없음), 교육용으로
  보이기·투명도·강조·맥동(심장·폐·위장 벽의 움직임 표현)을 GPU에서 바꿔 그린다. 팔 움직임 실험에서는 실제 근육
  메시를 팔꿈치 회전에 맞춰 GPU에서 변형해 보여 준다("움직임의 원리를 쉽게 관찰할 수 있도록 표현").
- 초등 교실용으로 외부 생식기 관련 구조는 숨김 처리한다.
- 기관·물질 아이콘(폐·위·콩팥·창자·산소·이산화 탄소 등)과 음식 삽화(김밥·우유·피자)는 이 프로젝트에서
  새로 그렸다(Lucide와 같은 24px·2px 선 규격).
- 《한입의 여행》 3D 음식 모형(김밥 한 조각·피자 한 조각·씹힌 조각·우유 액체)은 외부 파일 없이 코드로 직접 만들었다
  (`src/detail/foodModels.js`, docs/42).

## 2. 빌드에만 쓰는 도구(배포물에 코드가 들어가지 않음)

| 이름 | 용도 | 라이선스 |
|---|---|---|
| Vite 5 | 개발 서버·번들러 | MIT |
| vite-plugin-singlefile | 단일 HTML 실행 파일 만들기(모듈 로더 제거 옵션 사용) | MIT |
| puppeteer-core (프로젝트 밖 임시 폴더) | 화면 QA 스크린숏 | Apache-2.0 |

## 3. 쓰지 않은 것

- **Z-Anatomy**(CC BY-SA 4.0): 참고만 했고 통합하지 않았다(ShareAlike 조건 — 사용자 승인 없이 넣지 않음).
- 유료·출처 불명 3D 모델, 웹 폰트 파일: 포함하지 않는다(글꼴은 사용자 PC에 설치된 한글 글꼴을 쓴다).
- 교과서·실험관찰 원문 이미지: 포함하지 않는다(내용 기준으로만 사용).
- 외부 3D 음식 모델: Poly Haven(CC0) 모델 521개를 조회했으나 김밥·피자 조각·액체 우유가 없어 쓰지 않았다.
  로그인이 필요한 사이트(Sketchfab 등)와 유료 마켓은 조사·사용하지 않았다(docs/42 1절).
