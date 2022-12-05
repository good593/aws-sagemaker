# [SageMaker Pipeline Project](https://github.com/aws-samples/aws-ai-ml-workshop-kr/blob/master/sagemaker/sm-pipeline/amazon-sagemaker-reusable-components-kr/README.md)
![SageMaker Pipeline Project](./img/SageMaker%20Pipeline%20Project.png)

# 머신러닝 라이프 싸이클
![머신러닝 싸이클](./img/%EB%A8%B8%EC%8B%A0%EB%9F%AC%EB%8B%9D%20%EC%8B%B8%EC%9D%B4%ED%81%B4.png)
# SageMaker Pipeline
### 장점
![파이프라인 장점](./img/%ED%8C%8C%EC%9D%B4%ED%94%84%EB%9D%BC%EC%9D%B8%20%EC%9E%A5%EC%A0%90.png)
### 구성요소
![파이프라인 구성요소](./img/%ED%8C%8C%EC%9D%B4%ED%94%84%EB%9D%BC%EC%9D%B8%20%EA%B5%AC%EC%84%B1%EC%9A%94%EC%86%8C.png)
### 지원하는 스텝들
![파이프라인 지원 스텝들](./img/%ED%8C%8C%EC%9D%B4%ED%94%84%EB%9D%BC%EC%9D%B8%20%EC%A7%80%EC%9B%90%20%EC%8A%A4%ED%85%9D%EB%93%A4.png)
### 지표확인
![파이프라인 지표확인](./img/%ED%8C%8C%EC%9D%B4%ED%94%84%EB%9D%BC%EC%9D%B8%20%EC%A7%80%ED%91%9C%ED%99%95%EC%9D%B8.png)
### 실행내역
![실행내역](./img/%EC%8B%A4%ED%96%89%EB%82%B4%EC%97%AD.png)
### 모델 저장소
![모델 저장소](./img/%EB%AA%A8%EB%8D%B8%20%EC%A0%80%EC%9E%A5%EC%86%8C.png)
### 학습 평가
![학습평가](./img/%ED%95%99%EC%8A%B5%20%ED%8F%89%EA%B0%80.png)
### 모델 운영 반영 승인 과정
![모델 운영 반영 승인](./img/%EB%AA%A8%EB%8D%B8%20%EC%9A%B4%EC%98%81%20%EB%B0%98%EC%98%81%20%EC%8A%B9%EC%9D%B8.png)

# SageMaker Pipeline 만들기
![파이프라인 만들기](./img/%ED%8C%8C%EC%9D%B4%ED%94%84%EB%9D%BC%EC%9D%B8%20%EB%A7%8C%EB%93%A4%EA%B8%B0.png)
## 코드
```python
from sagemaker.inputs import TrainingInput
from sagemaker.workflow.steps import TrainingStep

# 스텝 생성
step_train = TrainingStep(
    name="TrainAbaloneModel",
    estimator=xgb_train,
    inputs={
        "train": TrainingInput(
            s3_data=step_process.properties.ProcessingOutputConfig.Outputs[
                "train"
            ].S3Output.S3Uri,
            content_type="text/csv"
        ),
        "validation": TrainingInput(
            s3_data=step_process.properties.ProcessingOutputConfig.Outputs[
                "validation"
            ].S3Output.S3Uri,
            content_type="text/csv"
        )
    }
)

from sagemaker.workflow.parameters import ParameterInteger, ParameterString, ParameterFloat

# 파라미터 설정
processing_instance_count = ParameterInteger(
    name="ProcessingInstanceCount",
    default_value=1
)

from sagemaker.workflow.pipeline import Pipeline

# 파이프라인 정의
pipeline_name = f"AbalonePipeline"
pipeline = Pipeline(
    name=pipeline_name,
    parameters=[
        processing_instance_count
    ],
    steps=[
        step_process, step_train, step_eval, step_cond
    ]
)
#Submit the pipeline definition
pipeline.upsert(role_arn=role)

# 파이프라인 실행
execution = pipeline.start()
# 파이프라인 실행 with 생성 변수
execution = pipeline.start(
    parameters=dict(
        ProcessingInstanceType="ml.c5.xlarge",
        ModelApprovalStatus="Approved"
    )
)

```