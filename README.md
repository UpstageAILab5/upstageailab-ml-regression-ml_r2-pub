[![Review Assignment Due Date](https://classroom.github.com/assets/deadline-readme-button-22041afd0340ce965d47ae6ef1cefeee28c7c493a6346c4f15d667ab976d596c.svg)](https://classroom.github.com/a/znc2XbtA)
# House Price Prediction | 아파트 실거래가 예측
## Team

| ![최진호](https://avatars.githubusercontent.com/u/40931237?s=88&v=4) | ![김남섭](https://avatars.githubusercontent.com/u/178737930?s=88&v=4) | ![김현진](https://avatars.githubusercontent.com/u/180828922?s=88&v=4) | ![박지은](https://avatars.githubusercontent.com/u/182731776?s=88&v=4) | ![송주은](https://avatars.githubusercontent.com/u/182833254?s=88&v=4) |
| :--------------------------------------------------------------: | :--------------------------------------------------------------: | :--------------------------------------------------------------: | :--------------------------------------------------------------: | :--------------------------------------------------------------: |
|            [최진호](https://github.com/lojino)             |            [김남섭](https://github.com/PotatoKim1)             |            [김현진](https://github.com/jinibizsite)             |            [박지은](https://github.com/FULLMOOONBY)             |            [오패캠](https://github.com/jsonghcbiz)             |
|                            팀장, 모델 선택 학습 및 평가                             |                            자료 수집                             |                            데이터 처리 , 모델 학습                             |                            데이터분석                             |                            데이터 분석 및 전처리                             |

## 0. Overview
### Environment
- [환경 설정 페이지](https://github.com/UpstageAILab5-Classroom/upstageailab5-ml-regression-ml_r2/blob/main/environment.md)

### Requirements
- [요구사항 페이지](https://github.com/UpstageAILab5-Classroom/upstageailab5-ml-regression-ml_r2/blob/main/requirements.txt)

## 1. Competiton Info

### Overview

- 2007년 1월부터 2023년 6월 데이터를 기반으로  2023년 7월부터   
  9월까지의 서울 아프트 실거래 가격을 예측하기위해 결측치와   
  이상치들을 다뤄봄으로써 전체적인 프로세스를 경험합니다.
- 높은 점수보단 개인 학습을 목표로 전처리부터 각자 한 번씩 
  실행해보면서 이해도를 높히는 쪽으로 방향을 잡았습니다.

### Timeline

- November 04, 2024 - Start Date
- November 14, 2024 - Final submission deadline

## 2. Components

### Directory

├── submit
│   ├── apartment_transaction_price_prediction.ipynb
│   │   
├── dev.jinhochoi
│   ├── apartment_transaction_price_prediction copy.ipynb
│   ├── balltree_haversine.ipynb
│   ├── balltree_haversion.csv
│   ├── unique_YX_poi.csv
│   └── unique_address.csv
├── jesong719
│   ├── data_pp_f.ipynb
│   ├── data_전처리_공유.ipynb
│   ├── kapt_crawl_step1.py
│   ├── kapt_crawl_step2.py
│   └── train_gis_merge.zip
├── jini.fullmoon
│   ├── baseline_code(현진님).ipynb
│   └── interestrate.csv
├── jinibizsite
│   ├── baseline_code_EDA.ipynb
│   ├── baseline_code.ipynb
│   ├── addressFinal.ipynb
│   ├── addrBusSubway.ipynb
│   └── XY버스지하철.zip
└── run5793
    └── test.txt

## 3. Data descrption

### Dataset overview

- _Explain using data_

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
continuous/categorical 변수 구분 [드랍 피쳐 결정]
'전화번호', '팩스번호', 'k-사용검사일-사용승인일', '수정일자', '고용보험관리번호', '청소비관리형태','단지승인일'
[파생변수 생성]

'구': tier1,2,3
'동': tier1,2,3,4
건축년도: new, mid, old, vold
[상관관계 화인]

[변수 보간]

train data 처리
train_dt2, test_dt2 생성 (is_test 컬럼 추가)
continuous/categorical 변수 구분
수치형 변수 보간
소수의 null값 보유 row 제거 : 아파트명, 번지
그룹화 선형회귀 모델 (데이터 : 그룹화 기준변수)
전체세대수 : 아파트명, 동
전체동수 : 아파트명, 동
주거전용면적 : 아파트명, 건축년도, 전용면적
연면적 : 아파트명, 건축년도, 전용면적
주차대수 : 전체세대수, 전용면적
전용면적<60, 전용면적60~85, 전용면적85~135 : 아파트명, 주거전용면적, 전용면적
주차대수 binning
관리비부과면적, 좌표X, 좌표Y, 건축면적, 단지신청일 제거

범주형 변수 보강
최빈값(mode)
세대타입, 관리방식, 경비비관리형태, 세대전기계약방법, 기타/의무/임대/임의, 사용허가여부, 관리비 업로드,
조건부 최빈값(conditional mode)
단지분류(전체동수, 주차대수)
복도유형(아파트명, 건축년도)
난방방식(아파트명, 건축년도, 전용면적)
[Encoding]

one-hot encoding: '사용허가여부', '시'
label encoding: '단지분류', '세대타입', '복도유형', '난방방식', '경비비관리형태', '세대전기계약방식', '관리비 업로드', '기타/의무/임대/임의=1/2/3/4', '주차대수'
frequency encoding: '아파트명','건설사', '구', '동', '계약년', '계약월'
target encoding :
[함수변환]

우선은 log 변환 적용
로그변환
제곱근변환

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
