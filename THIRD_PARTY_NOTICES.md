# 외부 자료, 출처 및 공개 범위

확인일: 2026-09-27. 이 문서는 확인한 제공자 표기와 이 저장소의 배포 범위를 기록합니다. 모든 권리 문제의 부재나 법적 적합성을 보증하는 문서는 아닙니다.

## 1. KcELECTRA

- 제작자: Junbum Lee / Beomi
- 저장소: https://github.com/Beomi/KcELECTRA
- 모델: https://huggingface.co/beomi/KcELECTRA-base
- 라이선스: MIT
- 원문: https://github.com/Beomi/KcELECTRA/blob/main/LICENSE

MIT는 이용·수정·배포를 허용하며, 해당 소프트웨어의 사본 또는 상당 부분을 배포할 때 저작권 고지와 허가 고지를 유지하도록 요구합니다. 이 저장소는 모델 가중치와 토크나이저를 재배포하지 않고 모델 식별자와 출처를 제공합니다. 추후 원본 코드·모델을 포함한다면 해당 MIT 전문과 저작권 고지를 함께 보존해야 합니다.

통합 및 동조 학습 코드에서 확인된 식별자는 `beomi/KcELECTRA-base`입니다. 이전 평가 자료에는 `Beomi/KcELECTRA-base-v2022`도 남아 있습니다. 정확한 학습 revision은 보관 자료만으로 확정하지 않았습니다.

## 2. Korean UnSmile 데이터셋

- 제공자: Smilegate AI; 공식 README는 데이터 태깅 및 검수 참여자로 언더스코어를 명시합니다.
- 원본: https://github.com/smilegate-ai/korean_unsmile_dataset
- 데이터 카드: https://huggingface.co/datasets/smilegate-ai/kor_unsmile
- 데이터 라이선스: CC BY-NC-ND 4.0
- 조건 요약: https://creativecommons.org/licenses/by-nc-nd/4.0/
- 법률 문서: https://creativecommons.org/licenses/by-nc-nd/4.0/legalcode.en
- 관련 논문: https://arxiv.org/abs/2204.03262

제공자 README는 데이터셋과 소스코드/baseline 모델의 라이선스를 구분합니다. 데이터셋에는 CC BY-NC-ND 4.0이, 제공자의 소스코드와 baseline 모델에는 Apache 2.0이 표시돼 있습니다. 데이터에 Apache 2.0을 적용하거나 KcELECTRA에 Unsmile의 baseline 모델 라이선스를 적용하지 않습니다.

CC BY-NC-ND 4.0은 저작자표시와 비영리 조건을 포함하고, 변경한 자료의 공유를 허용하지 않습니다. 라벨을 바꾸거나 텍스트를 정제한 CSV의 공개 가능성을 단순한 출처 표기만으로 해결할 수 있다고 보지 않습니다. 이 저장소는 **원문·가공 CSV·원문이 포함된 예측/오답 파일·해당 내용이 남은 노트북 출력**을 배포하지 않습니다. 공식 다운로드 경로와 처리 코드를 설명합니다.

학습 가중치의 배포 가능성은 데이터의 ND 조건만으로 일률적으로 단정할 수 없습니다. 이 공개본에는 가중치를 포함하지 않으며, 향후 배포나 상업적 활용 시에는 구체적 사용 방식과 제공자의 허락 범위를 별도로 확인해야 합니다. 이 저장소가 새로운 권한을 부여하지 않습니다.

## 3. 팀 구성 동조 데이터와 생성형 AI 보조

보관 라벨링 기준은 팀 원본과 Claude/Gemini 생성 예시를 사용했다고 기록합니다. 데이터 생성 시 사용한 계정 유형·약관 버전·입력 자료의 권리 범위는 보관 파일로 확정하지 못했습니다. 따라서 해당 데이터를 제3자에게 자유롭게 재배포할 수 있는 공개 데이터로 선언하지 않습니다.

원본 Excel, 생성 데이터, 가공 CSV, 샘플 텍스트가 담긴 보고서/출력은 이 저장소에 포함하지 않습니다. 방법론과 집계 수치만 설명합니다. 팀원은 저장소 소유자 외에는 익명으로 표기합니다.

## 4. 라이브러리와 외부 서비스

프로젝트는 PyTorch, Transformers, Datasets, scikit-learn, pandas, NumPy, safetensors, Gradio 등 외부 패키지를 사용합니다. 패키지 구현을 이 저장소에 복제하거나 포함하지 않습니다. 설치한 의존성에는 각 배포본의 라이선스가 적용됩니다.

Groq는 대화 생성용 외부 서비스입니다. KcELECTRA 분류 모델과 역할이 다릅니다. API 키를 제공하거나 생성 모델 가중치를 재배포하지 않습니다. API 이용에는 공급자의 해당 서비스 조건이 적용됩니다.

## 5. 팀 코드의 권리와 배포 정책

프로젝트는 4인의 공동 작업입니다. 정리한 사람을 전체 코드의 단독 저작자로 표시하지 않습니다. 팀 코드에 MIT/Apache 등 포괄적 재이용 허가를 새로 부여하지 않았습니다. 외부 자료의 기존 라이선스는 그대로 유지되며, 제3자의 코드 이용은 적용되는 권리와 허가 범위를 확인해야 합니다.

공개 대상은 README, 기술 설명, 정리된 노트북 코드와 CSS입니다. 제외 대상은 데이터, 모델 가중치·학습 상태, 실제 대화 DB, API 키, 개인 경로/공유 식별자, 원문을 포함한 실행 출력입니다. 발표 PDF는 코드와 다른 설명이 있어 그대로 배포하지 않고 검증된 설명을 README에 반영했습니다.
