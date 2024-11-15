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
```
├── submit
│   └── apartment_transaction_price_prediction.ipynb  
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
```

## 3. Data descrption

### Dataset overview

- 장소에 관련된 데이터들
  - 기본 데이터 : 시군구, 번지, 본번, 부번, 아파트명, 도로명, 좌표X, 좌표Y
  - 외부 데이터 : 위도, 경도, 주소, geometry, 건물명, 주소_amcc, 지번
- 아파트와 관련된 데이터들
  - 전용면적, 계약년월, 계약일, 층, 건축년도, 거래유형, k-단지분류, k-세대타입, k-관리방식, k-복도유형, k-난방방식, k-전체동수, k-전체세대수, k-건설사(시공사), k-시행사,k-사용검사일-사용승인일,k-연면적,k-주거전용면적,k-관리비부과면적,k-전용면적별세대현황(60㎡이하),k-전용면적별세대현황(60㎡~85㎡이하),k-85㎡~135㎡이하,k-135㎡초과, 건축면적, 주차대수, 기타/의무/임대/임의=1/2/3/4 등
- 많은 결측치들
![결측치](https://github.com/user-attachments/assets/21c9f916-be1c-4c13-8f2c-3533c6e06977)

### EDA

- 컬럼이름 변경 또는 변수 분할
- 계약년월 split : 계약년, 계약월
- 시군구 split : 시, 구, 동
- 각 column별 ' ', '-', 0 등 의미없는 값 결측치 처리
- 결측치 비율 확인
- 피쳐 드랍 : 1,000,000 이상 결측치 보유 피쳐 드랍 (dt_concat_select)
- 본번, 부번은 str으로 변환
- 중복 데이터 제거
- continuous/categorical 변수 구분
- 드랍 피쳐 결정 : '전화번호', '팩스번호', 'k-사용검사일-사용승인일', '수정일자', '고용보험관리번호', '청소비관리형태','단지승인일'
- 파생변수 생성
  - '구': tier1,2,3
  - '동': tier1,2,3,4
  - 건축년도: new, mid, old, vold

### Data Processing

- [변수 보간]

- train data 처리
  - train_dt2, test_dt2 생성 (is_test 컬럼 추가)
- continuous/categorical 변수 구분
  - 수치형 변수 보간
- 소수의 null값 보유 row 제거 : 아파트명, 번지
- 그룹화 선형회귀 모델 (데이터 : 그룹화 기준변수)
  - 전체세대수 : 아파트명, 동
  - 전체동수 : 아파트명, 동
  - 주거전용면적 : 아파트명, 건축년도, 전용면적
  - 연면적 : 아파트명, 건축년도, 전용면적
  - 주차대수 : 전체세대수, 전용면적
  - 전용면적<60, 전용면적60~85, 전용면적85~135 : 아파트명, 주거전용면적, 전용면적
  - 주차대수 binning
  - 관리비부과면적, 좌표X, 좌표Y, 건축면적, 단지신청일 제거

- 범주형 변수 보강
  - 최빈값(mode)
    - 세대타입, 관리방식, 경비비관리형태, 세대전기계약방법, 기타/의무/임대/임의, 사용허가여부, 관리비 업로드
  - 조건부 최빈값(conditional mode)
    - 단지분류(전체동수, 주차대수)
    - 복도유형(아파트명, 건축년도)
    - 난방방식(아파트명, 건축년도, 전용면적)
  
  
[Encoding]
- one-hot encoding: '사용허가여부', '시'
- label encoding: '단지분류', '세대타입', '복도유형', '난방방식', '경비비관리형태', '세대전기계약방식', '관리비 업로드', '기타/의무/임대/임의=1/2/3/4', '주차대수'
- frequency encoding: '아파트명','건설사', '구', '동', '계약년', '계약월'
- target encoding : '전용면적', '브랜드 등급'
  
[함수변환]
- 최초 로그 변환 적용


## 4. Modeling

### Model descrition
- LightGBM
  - 대규모 데이터를 빠르게 학습, 메모리 효율, 성능 면에서도 우수
  - Early Stopping을 지원하여 최적의 성능을 찾아줌 

### Modeling Process
- <img width="1143" alt="스크린샷 2024-11-15 오후 2 17 53" src="https://github.com/user-attachments/assets/04348fd1-af83-49da-b423-0a6c168c0c32">



## 5. Result

### Leader Board

- ![image](https://github.com/user-attachments/assets/be7cb81a-39f5-41e3-8349-a7352aa4674b)

- RMSE 31769.3940

### Presentation

- [발표 자료](https://docs.google.com/presentation/d/1txWIZLI-OGXhYKjVYKIvYTPcXxFFYP8uN2e7c6fmQtE/edit?usp=sharing)

## etc

### Meeting Log

- _Insert your meeting log link like Notion or Google Docs_

### Reference

- [(공유)도메인 지식을 기반으로 Geo 정보를 활용하는 방법](https://stages.ai/en/competitions/340/board/community/post/2842)
- [패스트캠퍼스 Upstage AI Lab 부트캠프 4기 아파트 가격예측 경진대회 후기](https://blog.naver.com/sejin_kwon/223590697466)
- [[업스테이지AILab 4기] 머신러닝, 부동산 가격 예측대회 회고](https://velog.io/@bzwear/%EC%97%85%EC%8A%A4%ED%85%8C%EC%9D%B4%EC%A7%80AILab-4%EA%B8%B0-%EB%A8%B8%EC%8B%A0%EB%9F%AC%EB%8B%9D-%EB%B6%80%EB%8F%99%EC%82%B0-%EA%B0%80%EA%B2%A9-%EC%98%88%EC%B8%A1%EB%8C%80%ED%9A%8C-%ED%9A%8C%EA%B3%A0)
