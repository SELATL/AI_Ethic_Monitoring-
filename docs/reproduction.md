# 실행 환경과 재현 범위

## 공개본의 성격

이 저장소는 기존 팀 프로젝트의 코드와 설명을 보존한 포트폴리오입니다. 데이터·가중치를 포함하지 않으며 현재 환경에서 전체 실행을 검증하지 않았습니다. 공개 노트북은 출력과 개인 경로를 정리한 사본입니다.

원본은 Google Colab에서 사용했습니다. GPU 사용을 전제로 한 학습 셀이 있고, `google.colab` 및 `!pip install` 구문이 있으므로 일반 Python 파일처럼 실행하는 구조가 아닙니다. 당시 앱 출력에는 PyTorch 2.11.0+cu128, Gradio 6.20.0이 기록돼 있고 모델 설정에는 Transformers 5.13.1이 남아 있으나, 이는 완전한 환경 잠금 파일이 아닙니다.

## 통합 데모

1. `notebooks/voda_dual_model_demo.ipynb`를 Colab에서 엽니다.
2. 경로 셀의 `PROJECT_PATH`를 자신의 프로젝트 폴더에 맞게 지정합니다. 공개용 기본 경로는 `/content/drive/MyDrive/voda-sentinel`입니다.
3. 적법하게 보유한 팀 학습 모델과 토크나이저를 아래 경로에 준비합니다. 원본 베이스 모델만으로 대체할 수 없습니다.

```text
voda-sentinel/
├── styles.css
├── models_3/kcelectra_v3_final/
│   ├── model.safetensors
│   ├── config.json
│   ├── tokenizer.json
│   └── tokenizer_config.json
└── syco_model/models/sycophancy_multitask_best/
    ├── model.safetensors
    ├── config.json
    ├── tokenizer.json
    └── tokenizer_config.json
```

4. 노트북의 환경 준비·모델 로딩·추론·저장소·UI 셀 순서를 확인합니다.
5. 대화 생성 기능에는 개인 Groq API 키가 필요합니다. 노트북은 `getpass` 입력을 사용합니다. 키를 코드에 직접 저장하지 마세요.
6. 마지막 실행 셀은 Gradio 공유 링크를 생성합니다. 자신의 실행에서 공개 공유 여부를 확인한 뒤 실행하세요. 외부 API에는 질문과 대화 이력이 전달되고 SQLite에는 질문·답변이 저장됩니다.

이 안내는 기존 구성 복원에 필요한 조건을 설명하며, 현재 공개본의 실행 성공을 보증하는 검증 기록은 아닙니다.

## 모델 A 전처리

`notebooks/unsmile_preprocessing.ipynb`는 공식 `smilegate-ai/kor_unsmile` 데이터를 로드해 8개 집단 혐오 카테고리, 정규식 욕설 신호 및 `clean` 조건으로 라벨을 생성하고 70/15/15로 분할합니다.

보관 실행 출력과 최종 CSV의 건수가 달라 이 코드가 발표 성능의 정확한 데이터 생성 버전이라고 단정할 수 없습니다. 원문과 변환 결과는 저장소에 커밋하지 않습니다. 사용 전 [Unsmile의 라이선스 조건](../THIRD_PARTY_NOTICES.md)을 확인해야 합니다.

## 모델 B 전처리·학습

- `sycophancy_preprocessing.ipynb`: 로컬 `sycophancy_dataset_combined_v4_1.xlsx`의 `data` 시트를 읽고 결측·공백·중복 정리, 심각도 매핑, 층화 분할을 수행합니다. 원본 Excel은 배포하지 않습니다.
- `sycophancy_training_evaluation.ipynb`: `data/processed/sycophancy_train.csv`와 `sycophancy_val.csv` 등을 읽고 KcELECTRA 멀티태스크 모델을 학습합니다. 개인 Drive 경로는 공개용 경로로 바꿨습니다.
- 남아 있는 설정은 최대 10 epoch, train batch 16, eval batch 32, learning rate `2e-5`, weight decay `0.01`, seed 42, early stopping patience 2입니다. 손실 가중치는 동조 1.0·편향 0.5·심각도 0.5입니다.
- 원본 노트북에는 학습 객체 생성 전의 평가 호출 등 실험용 셀이 남아 있습니다. 파일 첫 안내와 의존 관계를 확인해야 하며, 이 공개 정리에서 학습 절차를 재구현하거나 새 학습을 수행하지 않았습니다.

현재 동조 데이터의 생성형 AI 이용 조건과 배포 권한은 확정하지 못해 데이터를 제공하지 않습니다. 누구나 원본 데이터 없이 전체 결과를 재현할 수 있다고 주장하지 않습니다.
