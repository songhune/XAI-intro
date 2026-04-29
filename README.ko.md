# XAI-intro (Colab 우선)

이 저장소는 **로컬 Python 환경이 없어도 Google Colab에서 바로 실습**할 수 있도록 구성되어 있습니다.

## 문서 안내

- 영어 안내문: `README`
- 교수용 강의노트: `LECTURE_NOTES.ko.md`

## 1) Colab에서 시작하기

1. Google Colab을 엽니다: `https://colab.research.google.com`
2. `File -> Open notebook -> GitHub`로 이동합니다.
3. 이 저장소의 노트북을 엽니다.
4. 각 노트북의 **첫 번째 설치 셀**부터 실행합니다.
5. 설치 후 재시작 안내가 나오면 `Runtime -> Restart session`을 누른 뒤 다시 처음부터 실행합니다.

## 1.5) 비전공자용 아주 자세한 실행 순서

### A. 노트북 열기

1. Colab 페이지에 들어갑니다.
2. `File -> Open notebook`을 클릭합니다.
3. `GitHub` 탭을 클릭합니다.
4. 저장소를 검색하거나 URL을 붙여 넣습니다.
5. 먼저 `[0430]1.Decision_Tree_lab.ipynb`부터 여는 것을 권장합니다.

### B. 내 작업본 저장하기

1. `File -> Save a copy in Drive`를 클릭합니다.
2. 이후에는 Drive에 저장된 복사본에서 작업합니다.

### C. 코드 셀 1개 실행하기

1. 코드 셀 안을 클릭합니다.
2. 셀 왼쪽의 재생 버튼을 누르거나 `Shift + Enter`를 누릅니다.
3. 동그란 실행 표시가 멈출 때까지 기다립니다.
4. 셀 아래에 출력된 표, 숫자, 그래프를 읽습니다.

### D. 전체 셀 실행하기

1. `Runtime -> Run all`을 클릭합니다.
2. 위에서 아래로 순서대로 자동 실행됩니다.
3. 빨간 오류가 뜨면 설치 셀 또는 데이터 경로를 먼저 확인합니다.

### E. 설치 셀을 만났을 때

첫 설치 셀은 필요한 패키지를 설치합니다. 1~3분 정도 걸릴 수 있습니다.

재시작 메시지가 나오면:

1. `Runtime -> Restart session`
2. 다시 `Runtime -> Run all`

### F. 출력 읽는 법

- 표: 열 이름과 숫자의 범위를 먼저 봅니다.
- 그래프: 제목, x축, y축, 범례를 먼저 봅니다.
- 성능 지표: Accuracy, RMSE, F1이 무엇을 의미하는지 마크다운 설명과 같이 읽습니다.

### G. 가장 흔한 실수

- 중간 셀부터 먼저 실행하는 경우
- 설치 셀을 건너뛰는 경우
- 변수 이름을 실수로 바꾸는 경우
- 설치 후 런타임 재시작을 하지 않는 경우

막히면 가장 안전한 복구 방법:

1. `Runtime -> Restart session`
2. `Runtime -> Run all`

## 2) 권장 학습 순서

1. `[0430]1.Decision_Tree_lab.ipynb`
2. `[0430]2.Decision_Tree_solution.ipynb`
3. `[0430]3.Surrogate_lab.ipynb`
4. `[0430]4.Surrogate_solution.ipynb`

## 2.5) 데이터 폴더 규칙

모든 데이터 파일은 `data/` 폴더 아래에 있습니다.

- `data/wine.csv`
- `data/diabetes.csv`
- `data/pima-indians-diabetes.csv`

Colab에서는 업로드한 파일이 보통 `/content` 아래로 들어갑니다. 가능하면 `/content/data`로 옮겨서 사용하세요.

```bash
mkdir -p /content/data
mv /content/wine.csv /content/data/wine.csv
```

노트북은 아래 순서로 경로를 찾도록 구성되어 있습니다.

1. `/content/data/...`
2. `./data/...`
3. `../data/...`

## 3) Colab 의존성 안내

최근 Colab 환경에서는 다음과 같은 문제가 자주 생깁니다.

- NumPy 2.x 전환에 따른 호환성 문제
- `shap`와 `xgboost`의 버전 조합 문제
- 설치 후 런타임 재시작이 필요한 문제

이를 줄이기 위해 Surrogate 노트북은 설치 셀에서 버전을 고정했습니다.

```python
lime==0.2.0.1
scikit-image==0.25.2
shap==0.46.0
xgboost==2.1.4
```

## 4) 의존성 점검 결과

점검 범위:

- 전체 `*.ipynb` 파일 스캔
- Surrogate 노트북의 설치/호환성 셀 확인

확인된 사항:

- Surrogate lab/solution 노트북에 설치 셀이 있습니다.
- `%%time` 대신 `perf_counter`를 사용하도록 정리되어 있습니다.
- Boston 데이터셋은 `fetch_openml` fallback을 고려하도록 정리되어 있습니다.
- Decision Tree 노트북은 Colab 실행을 고려해 데이터 경로를 `data/` 기준으로 찾도록 수정했습니다.

## 5) 문제 해결

### `ModuleNotFoundError`가 나올 때

1. 설치 셀을 다시 실행합니다.
2. 런타임을 재시작합니다.
3. 위에서부터 다시 실행합니다.

### 설치는 됐는데 예전 버전처럼 동작할 때

이미 메모리에 올라간 오래된 모듈이 남아 있는 경우가 많습니다. 런타임을 재시작하세요.

### Colab 세션이 끊길 때

Colab 세션은 휘발성이므로 중간중간 Drive에 저장하세요.

## 6) 실행 원칙

- 셀은 항상 **위에서 아래로** 실행합니다.
- 제출 전에는 `Restart session -> Run all`로 재현성을 확인합니다.
- 설치 셀은 삭제하지 않는 것이 좋습니다.