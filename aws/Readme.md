# Sagemaker 실습코드

본 폴더는 SageMaker를 다양한 기능을 실습할 수 있는 예제를 포함하고 잇습니다.

---
## 1. SageMaker 를 이용한 ML/DL 모델 개발과 추론

#### 1-1. 빌트인 알고리즘 활용하기

- 생략

#### 1-2. BYOS (Bring Your Own Script)

- [Tensorflow script mode 사용하기](byos-tensorflow/Readme.md) - SageMaker에서 제공하는 Tensorflow 컨테이너를 이용하여 보스톤지역의 집값을 예측하는 회귀모델을 만들고 활용해 봅니다. [바로가기](byos-tensorflow/Readme.md) 

#### 1-3. BYOC (Bring Your Own Container)

- [BYOC Scikit-learn](byoc/scikit_bring_your_own/scikit_bring_your_own.ipynb) - SageMaker 커스텀 컨테이너로 생성하는 방법을 이해할 수 있습니다. 예제코드는 Scikit-learn을 이용한 붓꽃 품종을 분류하는 간단한 모델을 이용합니다.[바로가기](byoc/scikit_bring_your_own/scikit_bring_your_own.ipynb)

#### 1-4. BYOM (Bring Your Own Model)

- [Tensorflow deployment](tf-deploy/README.md) - Tensorflow Serving 실습 [바로가기](tf-deploy/README.md)

#### 1-5. SageMaker Ground Truth

- [Hello GroundTruth](hello-gt/README.md) - SageMaker GroundTruth 시작하기 [바로가기](hello-gt/README.md)

#### 1-6. SageMaker Data Wrangler


---

## 2. SageMaker 고급기능 활용하기

#### 2-1. SageMaker Debugger

#### 2-2. SageMaker Distributed Training

#### 2-3. SageMaker Clarify

#### 2-4. SageMaker Feature Store


---

## 3. SageMaker MLOps 적용하기

#### 3-1. SageMaker Pipeline

#### 3-2. SageMaker Project
- [SageMaker Pipeline](sm-pipeline/README.md) - SageMaker Pipeline & Project 실습 [바로가기](sm-pipeline/README.md)

#### 3-3. SageMaker Model monitor

- [SageMaker Model Monitor](model-monitor/SageMaker-ModelMonitoring.ipynb) SageMaker Model Monitor 기능 체험 [바로가기](model-monitor/SageMaker-ModelMonitoring.ipynb)

---
## 4. SageMaker 보안 & 거버넌스

#### 4-1. SageMaker ABAC

#### 4-2. Sagemaker Multi account deployment


---
## 5. SageMaker를 이용한 머신러닝/딥러닝 문제해결

#### 5-1. SageMaker Canvas (No code 머신러닝)
- [SageMaker Canvas 공식 실습가이드(영문)](https://catalog.us-east-1.prod.workshops.aws/workshops/80ba0ea5-7cf9-4b8c-9d3f-1cd988b6c071/en-US/)
- [AWS Glue DataBrew와 SageMaker Canvas를 이용한 No code 머신러닝 모델 개발/적용](canvas-and-glue-databrew/Readme.md)

#### 5-2. AutoML
- [AutoGluon Hello World!](autogluon/autogluon_helloworld.ipynb) - 오픈소스 AutoGluon의 Getting Started 예제입니다. [바로가기](autogluon/autogluon_helloworld.ipynb)
- [Code Free Auto Gluon](autogluon/README.md) - 람다와 SageMaker 커스텀 컨테이너를 이용하여 AutoGluon 실행하기 [바로가기](autogluon/README.md)




