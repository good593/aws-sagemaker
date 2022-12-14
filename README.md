# [Operationalizing the Machine Learning Pipeline](https://catalog.us-east-1.prod.workshops.aws/workshops/44d3e2a0-ec6f-44df-9397-bcfdf129cadf/en-US)
- Overview
    > In this workshop you will build an MLOps pipeline that leverages Amazon SageMaker, a service that supports the an entire pipeline for ML model development, and is the heart of this solution. Around it, you will add different AWS DevOps tools and services to create an automated CI/CD pipeline for the ML model. This pipeline will prepare the data, build your docker images, train and test the ML model, and the integrate the model into a production workload.

- Services & Skills
    - Training and Testing an ML model
    - Python3
    - Docker
    - SageMaker, CodePipeline, ECR, Cloud9, CloudFormation, Lambda, Step Functions, S3
### [Introduction](https://catalog.us-east-1.prod.workshops.aws/workshops/44d3e2a0-ec6f-44df-9397-bcfdf129cadf/en-US/module-introduction-1)
- Architecture
### [Configure Pipeline Data Repositories](https://catalog.us-east-1.prod.workshops.aws/workshops/44d3e2a0-ec6f-44df-9397-bcfdf129cadf/en-US/module-configure-pipeline-data-repositories-2)
- Training Data Bucket
- ETL Data Bucket
- CodeCommit Repository
- Container Image Repository
### [Configuring Pipeline Assets](https://catalog.us-east-1.prod.workshops.aws/workshops/44d3e2a0-ec6f-44df-9397-bcfdf129cadf/en-US/module-configuring-pipeline-assets-3)
- ETL Job Assets
- Training and Inference Assets
- Running Unit Tests
- System Test Assets
### [Creating and Executing the Pipeline](https://catalog.us-east-1.prod.workshops.aws/workshops/44d3e2a0-ec6f-44df-9397-bcfdf129cadf/en-US/module-creating-and-executing-the-pipeline-4)
- Creating the Pipeline
- Executing the Pipeline
### [Managing the Production Deployment](https://catalog.us-east-1.prod.workshops.aws/workshops/44d3e2a0-ec6f-44df-9397-bcfdf129cadf/en-US/module-managing-the-production-deployment-5)
- Simulate Load
- Monitoring Endpoint Performance
- Monitoring Model Drift

# [AWS AIML 스페셜 웨비나 2022](https://www.youtube.com/playlist?list=PLORxAVAC5fUULZBkbSE--PSY6bywP7gyr)
- [2022 웹비나 예제 소스](./aws/sm-special-webinar/README.md)

## amazon SageMaker Studio
- 참고 자료
    - https://github.com/daekeun-ml/sagemaker-studio-workshop-kr

## [Amazon SageMaker Training](./training/README.md)
- 완전 관리형 머신 러닝 학습 서비스
- 학습 코드에 분산 라이브러리를 추가한 후, 인스턴스의 수를 늘리면 분산학습이 바로 동작
- 참고자료
    - https://github.com/aws-samples/aws-ai-ml-workshop-kr/tree/master/sagemaker
    - [tensorflow](https://github.com/daekeun-ml/tensorflow-in-sagemaker-workshop)
    - [pytorch](https://github.com/daekeun-ml/end-to-end-pytorch-on-sagemaker)
    - [시계열 추론](https://github.com/daekeun-ml/time-series-on-aws-hol)
    - [NLP](https://github.com/daekeun-ml/sm-huggingface-kornlp)

## [Amazon SageMaker Experiments](./experiments/README.md)
- 실험의 여러 시도에 대해 사용자의 하이퍼파라미터, 평가 지표 등을 기록 및 추적

## [Amazon SageMaker Processing](./processing/README.md)
- 데이터의 사전 처리, 모델 결과의 후처리 및 모델 평가를 실행할 수 있는 컴퓨팅 환경을 제공

## [Amazon SageMaker Deploy](./deploy/README.md)
- 참고자료
    - [4개 추론 예제](https://github.com/aws-samples/sm-model-serving-patterns)
    - [엔드포인트 또는 컴파일 예제](https://github.com/aws-samples/sagemaker-inference-samples-kr)
    - [Nvidia Jetson Nano](https://github.com/aws-samples/aiot-e2e-sagemaker-greengrass-v2-nvidia-jetson)

## [Amazon SageMaker Pipeline](./pipeline/README.md)
- 스케일이 가능하고 완전 자동화된 머신러닝 워크플로 구축
- 참고자료
    - https://github.com/gonsoomoon-ml/SageMaker-Pipelines-Step-By-Step

# 기타
- [개발 가이드](https://docs.aws.amazon.com/sagemaker/latest/dg/deploy-model.html)
- [SageMaker Python SDK](https://sagemaker.readthedocs.io/en/stable/overview.html)
