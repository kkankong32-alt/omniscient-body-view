# 에셋 및 라이브러리 출처 (Attribution)

> 현재 상태(2026-09-28, SCIENCE-SAFE UX + CINEMATIC DETAIL): 앱은 **BodyParts3D 4.0 IS-A 전체 2,234 메시**를
> Human Atlas(MIT)가 브라우저용으로 변환한 atlas(`public/atlas/atlas.json` + `body-0..14.bin.gz`)로 그린다.
> 뼈(손·발뼈 포함)·근육·소화·호흡·배설 기관·심장·혈관·피부가 모두 실제 데이터이며, 입(혀·이)·코·항문도
> 실제 구조로 잡는다. 전체 제3자 목록은 `THIRD_PARTY_NOTICES.md`.

## 3D 인체 모델 — BodyParts3D Release 4.0

- **원본**: BodyParts3D Release 4.0, IS-A Tree, 99% 폴리곤 감소판(`isa_BP3D_4.0_obj_99.zip`) — 2,234 메시, 약 229만 삼각형
- **제작**: Database Center for Life Science (DBCLS)
- **참조 신체**: 성인 남성(공식 README 명시) — 앱 안에서는 "인체 모형"으로만 지칭한다.
- **라이선스**: **Creative Commons Attribution 4.0 International (CC BY 4.0)**
- **필수 출처 문구**: "BodyParts3D, © The Database Center for Life Science licensed under CC Attribution 4.0 International"
- **브라우저용 변환**: Human Atlas(github.com/ashemag/human-atlas @1c38bf3, **MIT**)의 atlas 형식(좌표 m 단위, 파트별
  위치·법선·인덱스를 gzip 청크로 묶음)을 그대로 쓴다. 앱은 atlas 루트에 좌표 오프셋 하나만 적용한다(개별 기관 재배치 없음).
- **가공 사실**: 원본 메시 형태는 바꾸지 않는다. 재질(색)은 앱이 입히며, 정맥을 파랗게 칠하지 않는다(과학 LOCK).
  교육용 보이기·투명도·강조·맥동은 GPU 상태로만 바꾼다. 외부 생식기 관련 구조는 초등 교실용으로 숨긴다.
- **교과서 기관 ↔ 메시 매핑**: `src/data/anatomySource.js`(FMA concept id)와 `src/atlas/atlasRegistry.js`(이름 규칙:
  손·발뼈, 어깨·골반뼈, 혀·이, 코 연골, 바깥항문조임근). 검증: `src/core/validateAtlas.js`(npm run check).
- **팔 움직임 실험**: atlas의 실제 오른팔 — 위팔뼈·노뼈·자뼈·손뼈 27개, 위팔두갈래근(2)·위팔근(팔 안쪽 근육),
  위팔세갈래근(3)(팔 바깥쪽 근육). 근육 길이 변화·굵어짐은 실제 메시를 팔꿈치 회전에 맞춰 변형한 **교육용 표현**이며,
  화면에 "BodyParts3D의 실제 인체 구조를 바탕으로, 움직임의 원리를 쉽게 관찰할 수 있도록 표현했습니다."라고 안내한다.
- **교육용 확대 표현**: 작은창자 벽·폐 속·콩팥 속처럼 atlas에 없는 미세 구조는 3D로 지어내지 않고, 화면 오른쪽 위
  원형 렌즈에 "교육용 확대 표현"이라고 표시한 2D 그림으로만 보여 준다.

**라이선스 확인 경위**: DBCLS의 현재(2025-02-27 갱신) 공식 License 페이지와 LATEST README로 확인했다(CC BY 4.0,
ShareAlike 의무 없음). 한때 구버전 조건(CC BY-SA 2.1 Japan)을 잘못 적었던 정정 경위는 `docs/DECISIONS.md` D-001·D-005,
`docs/10_LICENSE_VERIFICATION.md`.

### 이전 자산(lineage 기록)

재건 전(git 태그 `pre-opus55-rebuild`)에는 기관별 GLB 23개(`public/anatomy/organs/`)를 썼다. 지금 앱은 이 파일들을
읽지 않으며, FMA 매핑 표의 출처 기록으로만 남긴다. 팔 실험 전용 GLB 2개(`public/anatomy/experiment/`)는 atlas 팔로
바꾸면서 삭제했다.

## 오픈소스 라이브러리

| 라이브러리 | 용도 | 라이선스 |
|---|---|---|
| [three.js](https://threejs.org) 0.166 | 3D 렌더링 | MIT |
| [Lucide](https://lucide.dev) 1.48 (아이콘 경로 일부) | UI 아이콘 | ISC |
| [Vite](https://vitejs.dev) · vite-plugin-singlefile | 개발 서버·번들러(배포물에 미포함) | MIT |

## 교과 내용 근거

- 2022 개정 교육과정 초등과학 5-1 4단원 「우리 몸의 구조와 기능」 교과서(86~111쪽) 및 실험관찰(52~67쪽)
  ※ 교과서·실험관찰 원문 이미지는 저장소에 포함하지 않는다(`_reference/`는 `.gitignore`로 제외).

## 코드 라이선스

이 프로젝트 코드 자체의 오픈소스 라이선스는 아직 선언하지 않는다(docs/DECISIONS.md D-003).

## 개인정보

- 로그인 없음, 학생 이름·학번 미수집, 서버 전송 없음.
- 관찰 기록은 이 기기의 브라우저 저장소(localStorage)에만 저장된다. 저장소가 막힌 환경(파일로 열기·시크릿 창)에서도
  앱은 멈추지 않고, 기록이 저장되지 않는다는 안내만 보여 준다.
- 이 앱은 의료기기가 아니며 건강 상태를 진단하지 않는다.
