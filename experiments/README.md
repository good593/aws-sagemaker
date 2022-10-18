# Experiments 설명
![Experiment, Trial](./img/Experiment%2C%20Trial.png)

# [코드 예시](https://aws.amazon.com/ko/blogs/aws/amazon-sagemaker-experiments-organize-track-and-compare-your-machine-learning-trainings/)
![코드 예시](./img/experiment%2C%20trail%20%EC%BD%94%EB%93%9C%20%EC%98%88%EC%8B%9C.png)

# 평가지표
![평기지표 정의](./img/metric%20definitions.png)
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

metric_definitions = [
    {'Name': 'train:Loss', 'Regex': 'Train_Loss = (.*?) :'}
]

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
    # metric definitions
    metric_definitions=metric_definitions
)
```

# Experiments 콘솔 정보
![정보들](./img/experiments%20%EC%A0%95%EB%B3%B4%EB%93%A4.png)

