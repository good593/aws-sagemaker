# 학습 동작 원리
![학습 동작 원리](./img/%ED%95%99%EC%8A%B5%20%EB%8F%99%EC%9E%91%20%EC%9B%90%EB%A6%AC.png)
  
# 학습 코드
### [학습코드 내 경로](https://github.com/aws/sagemaker-training-toolkit/blob/master/ENVIRONMENT_VARIABLES.md)
![input, code](./img/%ED%95%99%EC%8A%B5%EC%BD%94%EB%93%9C%20%EB%82%B4%20%EA%B2%BD%EB%A1%9C(input%2C%20code).png)
![model, output, checkpoints](./img/%ED%95%99%EC%8A%B5%EC%BD%94%EB%93%9C%20%EB%82%B4%20%EA%B2%BD%EB%A1%9C(model%2C%20output%2C%20checkpoints).png)
![code](./img/%ED%95%99%EC%8A%B5%EC%BD%94%EB%93%9C%20%EB%82%B4%20%EA%B2%BD%EB%A1%9C%20%EC%88%98%EC%A0%95%20%EC%BD%94%EB%93%9C.png)
  
### 학습 코드 예제
#### Pytorch
```python
import sagemaker
from sagemaker.pytorch import Pytorch

sagemaker_session = sagemaker.Session()
role = sagemaker.get_execution_role()

hyperparameters = {
    "batch_size":32,
    "lr":1e-4,
    "image_size":128
} # 모델에 따라 다름

estimator = Pytorch(
    # 필수 파라미터
    source_dir="code",                      # dir of files
    entry_point="train.py",                 # file for train
    role=role,                              # aws iam role
    framework_version="1.10",               # pytorch version
    py_version="py38",                      # python version
    instance_count=1,                       # train instance count
    instance_type="ml.p4d.24xlarge",        # train instance type
    sagemaker_session=sagemaker_session,    # SageMaker Session
    hyperparameters=hyperparameters,        # hyperparameters
    # 옵션 파라미터     
    max_run=5*24*60*60,                     # 5일; 최대 학습 수행 시간(초)
    use_spot_instances=True,                # spot 인스턴스 사용 유무
    max_wait=3*60*60,                       # 3시간; spot 사용 시 자원 재확보를 위한 대기 시간
    checkpoint_s3_uri=checkpoint_s3_uri     # checkpoints 저장 s3 위치
)

channel_name = "training"
# s3인 경우
data_path = "s3://my_bucket/my_training_data/"
# EFS인 경우
data_path = FileSystemInput(
                file_system_id='fs-1', file_system_type='EFS',
                directory_path='/dataset', file_system_access_mode='ro'
            )
# FSx for Lustre인 경우
data_path = FileSystemInput(
                file_system_id='fs-2', file_system_type='FSxLustre',
                directory_path='/<mount-id>/dataset', file_system_access_mode='ro'
            )

estimator.fit(
    inputs={
        channel_name : data_path,
    },
    job_name=job_name
)
```

# 학습 디버깅
![학습 디버깅](./img/%ED%95%99%EC%8A%B5%20%EB%94%94%EB%B2%84%EA%B9%85.png)
### 디버깅용 학습 코드
```python
# Local Mode(디버깅 모드)
from sagemaker.local import LocalSession
from pathlib import Path

sagemaker_session = LocalSession()                      # Local 세션 설정
sagemaker_session.config = {
    'local' : {'local_code':True}
}
data_path = f'file://{Path.cwd()}/dataset'              # Notebook 인스턴스 내 데이터셋 경로
source_dir = f'{Path.cwd()}/{source_code_directory}'    # 학습 스크립트가 들어 있는 폴더 경로
checkpoint_s3_bucket = None
instance_type = 'local'                             # 인스턴스 타입; gpu인 경우(local_gpu)

# Train Mode
from sagemaker

sagemaker_session = sagemaker.Session()                     # SageMaker 세션 설정
source_dir = f'{source_code_directory}'                     # 학습 스크립트가 들어 있는 폴더 경로
checkpoint_s3_bucket = f's3://{result_bucket}/checkpoints'  # Checkpoint 파일 저장 위치
instance_type = 'ml.p4d.24xlarge'                           # 인스턴스 타입

```

# 학습 모니터링
![모니터링](./img/%EB%AA%A8%EB%8B%88%ED%84%B0%EB%A7%81.png)