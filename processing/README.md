# Processing 동작 원리
![동작원리](./processing%20%EB%8F%99%EC%9E%91%EC%9B%90%EB%A6%AC.png)
![동작원리 with s3](./processing%20%EB%8F%99%EC%9E%91%EC%9B%90%EB%A6%AC%20with%20s3.png)

# Processing 예제 코드
```python
from sagemaker.sklearn.precessing import SKLearnProcessor
from sagemaker.processing import Processor, ScriptProcessor, FrameworkProcessor

import sagemaker
from sagemaker.pytorch import Pytorch

sagemaker_session = sagemaker.Session()
role = sagemaker.get_execution_role()

processor = FrameworkProcessor(
                PyTorch, framework_version="1.10", role=role,
                instance_type="ml.g5.xlarge", instance_count=1
            )

from sagemaker.processing import ProcessingInput, ProcessingOutput

processor.run(
    code = "preprocessing.py",
    inputs = [
        ProcessingInput(
            source=INPUT_S3_URI, destination="/opt/ml/processing/input"
        )
    ],
    outputs = [
        ProcessingOutput(
            source="/opt/ml/processing/output/train", destination=OUTPUT_S3_URI_1
        ),
        ProcessingOutput(
            source="/opt/ml/processing/output/validation", destination=OUTPUT_S3_URI_2
        )
    ]
)

```

