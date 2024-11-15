[![Review Assignment Due Date](https://classroom.github.com/assets/deadline-readme-button-22041afd0340ce965d47ae6ef1cefeee28c7c493a6346c4f15d667ab976d596c.svg)](https://classroom.github.com/a/znc2XbtA)
# House Price Prediction | 아파트 실거래가 예측
## Team

| ![최진호](https://avatars.githubusercontent.com/u/40931237?s=88&v=4) | ![김남섭](https://avatars.githubusercontent.com/u/178737930?s=88&v=4) | ![김현진](https://avatars.githubusercontent.com/u/180828922?s=88&v=4) | ![박지은](https://avatars.githubusercontent.com/u/182731776?s=88&v=4) | ![송주은](https://avatars.githubusercontent.com/u/182833254?s=88&v=4) |
| :--------------------------------------------------------------: | :--------------------------------------------------------------: | :--------------------------------------------------------------: | :--------------------------------------------------------------: | :--------------------------------------------------------------: |
|            [최진호](https://github.com/lojino)             |            [김남섭](https://github.com/PotatoKim1)             |            [김현진](https://github.com/jinibizsite)             |            [박지은](https://github.com/FULLMOOONBY)             |            [오패캠](https://github.com/jsonghcbiz)             |
|                            팀장, 모델 선택 학습 및 평가                             |                            자료 수집                             |                            데이터 처리 , 모델 학습                             |                            데이터분석                             |                            데이터 분석 및 전처리                             |

## 0. Overview
### Environment
- _Write Development environment_

### Requirements
- _Write Requirements_

## 1. Competiton Info

### Overview

- _Write competition information_

### Timeline

- ex) January 10, 2024 - Start Date
- ex) February 10, 2024 - Final submission deadline

## 2. Components

### Directory

- _Insert your directory structure_

e.g.
```
├── code
│   ├── jupyter_notebooks
│   │   └── model_train.ipynb
│   └── train.py
├── docs
│   ├── pdf
│   │   └── (Template) [패스트캠퍼스] Upstage AI Lab 1기_그룹 스터디 .pptx
│   └── paper
└── input
    └── data
        ├── eval
        └── train
```

## 3. Data descrption

### Dataset overview

- _Explain using data_
Data 전처리
[기본 환경 설정]
[데이터 불러오기]
[Train/Test 구분 및 합치기]
dt_concat
[dt_concat 기본 전처리]

컬럼이름 변경 또는 변수 분할
컬럼 이름 변경
변수 분할
계약년월 split : 계약년, 계약월
시군구 split : 시, 구, 동
각 벌럼펼 ' ', '-', 0 등 의미없는 값 결측치 처리
결측치 비율 확인
피쳐 드랍
1,000,000 이상 결측치 보유 피쳐 드랍 (dt_concat_select)
본번, 부번은 str으로 변환
중복 데이터 제거
continuous/categorical 변수 구분 [드랍 피쳐 결정
### EDA

- _Describe your EDA process and step-by-step conclusion_

### Data Processing

- _Describe data processing process (e.g. Data Labeling, Data Cleaning..)_

## 4. Modeling

### Model descrition

- _Write model information and why your select this model_

### Modeling Process

- _Write model train and test process with capture_

## 5. Result

### Leader Board

- _Insert Leader Board Capture_
- _Write rank and score_

### Presentation

- _Insert your presentaion file(pdf) link_

## etc

### Meeting Log

- _Insert your meeting log link like Notion or Google Docs_

### Reference

- _Insert related reference_
