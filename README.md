# KMU Brain TabNet

KMU Brain 프로젝트에서 TabNet 기반 tabular classification 실험을 수행한 노트북 저장소입니다.

## Tech Stack

- Python
- PyTorch
- pytorch-tabnet
- pandas / NumPy
- scikit-learn
- matplotlib
- Jupyter Notebook

## Results / Highlights

- 의료/생체 tabular feature를 대상으로 TabNet 분류 실험을 구성했습니다.
- RobustScaler, MinMaxScaler, StandardScaler 기반 전처리 후보를 비교할 수 있도록 노트북에 정리했습니다.
- AUC와 logloss를 validation metric으로 사용하고, best epoch와 best validation AUC를 산출하는 흐름을 구현했습니다.
- feature drop 후보(`drop_cols_best`)를 별도로 관리해 모델 입력 변수 선택 실험을 반복할 수 있게 했습니다.

## Project Structure

```text
.
├── notebooks/
│   ├── kmu_model.ipynb
│   └── tabnet_experiment.ipynb
├── requirements.txt
└── README.md
```

## Private Data

원본 데이터, 학습 결과, 체크포인트는 포함하지 않습니다. 노트북 실행 시 필요한 CSV 또는 피처 파일은 로컬 `data/` 폴더에 배치합니다.

```text
data/
└── your_dataset.csv
```

## Setup

```bash
python -m venv .venv
source .venv/bin/activate
pip install -r requirements.txt
jupyter lab
```

## Notes

- 이 저장소는 노트북 중심의 실험 기록입니다.
- `data/`, `outputs/`, `models/`, checkpoint 파일은 Git 추적 대상에서 제외됩니다.

## Lessons / Improvements

- tabular medical data에서는 scaling, feature dropping, validation AUC를 함께 관리해야 실험 비교가 쉬워집니다.
- 다음 단계에서는 notebook 실험을 `src/train.py` 형태로 모듈화하고, best metric과 feature set을 별도 결과 파일로 저장할 수 있습니다.
