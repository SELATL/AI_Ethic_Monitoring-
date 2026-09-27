# 보관 자료와 공개용 파일의 대응

원본 Google Drive 폴더는 수정하지 않았습니다. 공개용 사본에는 노트북 출력, 실행 횟수, Colab/위젯 등 불필요한 메타데이터, 개인 공유 폴더 식별자를 남기지 않았습니다. 경로는 `/content/drive/MyDrive/voda-sentinel` 기준으로 일반화했습니다. 모델·학습·추론 함수의 동작을 개선했다고 주장하지 않습니다.

| 보관 자료 | 공개용 파일 |
|---|---|
| `VODA_Sentinel_AI_Governance_Platform_v1.1_dual_model.ipynb` | `notebooks/voda_dual_model_demo.ipynb` |
| `data3/data_preprocessing_2.ipynb` | `notebooks/unsmile_preprocessing.ipynb` |
| `syco_model/scripts/전처리_.ipynb` | `notebooks/sycophancy_preprocessing.ipynb` |
| `syco_model/scripts/syco_성능평가.ipynb` | `notebooks/sycophancy_training_evaluation.ipynb` |
| `styles.css` | `styles.css` |

모델 B 노트북 이름은 평가를 뜻하지만, 실제로 학습 정의와 `trainer.train()`도 포함하므로 공개 사본 이름에 training을 함께 표기했습니다. 보관용 안내 셀을 추가하고 출력은 삭제했습니다. 출력에 남아 있던 평가 규모와 집계값은 `docs/evidence.md`에 따로 설명합니다.

## 이번 공개본에서 제외한 자료

- 데이터 원문·CSV·Excel·ZIP: 외부 데이터 라이선스와 자체 동조 데이터의 권리 범위 때문
- 모델 가중치·토크나이저·학습 상태: 이번 코드 중심 공개 범위에서 제외
- 실제 SQLite DB: 사용자 질문·AI 답변 기록 포함
- 예측·오답 텍스트와 기존 노트북 실행 출력: 데이터 원문·개인 경로 포함 가능
- v1.0 Colab 내보내기 Python 파일 및 중복 사본: 대표 구현인 v1.1과 중복되어 제외
- `.gdoc` 바로가기: 문서 본문이 아니며 개인 계정·문서 식별자 포함
- 발표 PDF 원본: 당시 설명과 현재 보관 코드의 불일치가 있어 검증한 내용을 문서에 반영

이 목록에서 제외됐다고 원본이 삭제된 것은 아닙니다. 과거 자료가 부족한 부분을 새 코드로 만들어 당시의 구현처럼 대체하지 않았습니다.
