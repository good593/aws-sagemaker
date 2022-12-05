# 클라우드 네이티브 모델 장점
![네이티브 모델 장정](./img/%ED%81%B4%EB%9D%BC%EC%9A%B0%EB%93%9C%20%EB%84%A4%EC%9D%B4%ED%8B%B0%EB%B8%8C%20%EB%AA%A8%EB%8D%B8%20%EC%9E%A5%EC%A0%90.png)

# SageMaker 전체 프로세스
![전체 프로세스](./img/%EC%A0%84%EC%B2%B4%20%EB%B0%B0%ED%8F%AC%20%ED%94%84%EB%A1%9C%EC%84%B8%EC%8A%A4.png)
![모델 서빙 동작원리](./img/%EB%AA%A8%EB%8D%B8%20%EC%84%9C%EB%B9%99%20%EB%8F%99%EC%9E%91%EC%9B%90%EB%A6%AC.png)

## 모델
![모델 빌드](./img/%EB%AA%A8%EB%8D%B8%20%EB%B9%8C%EB%93%9C.png)

## [엔드포인트](./endpoint.md)
![4개 추론 요약](./img/4%EA%B0%9C%20%EC%B6%94%EB%A1%A0%20%EC%9A%94%EC%95%BD.png)
### [endpoint with api gateway](https://aws.amazon.com/ko/blogs/korea/creating-a-machine-learning-powered-rest-api-with-amazon-api-gateway-mapping-templates-and-amazon-sagemaker/)

# 엘라스틱 추론
![엘라스틱 추론 설명](./img/%EC%97%98%EB%9D%BC%EC%8A%A4%ED%8B%B1%20%EC%B6%94%EB%A1%A0%20%EC%84%A4%EB%AA%85.png)

# AWS SDK
### Deploy
![deploy with sdk](./img/deploy%20with%20sdk.png)

### Predictor
```python
from sagemaker.serializers import CSVSerializer

xgb_predictor = xgb.deploy(
                    initial_instance_count=1, # returns predictor object
                    instance_type="ml.m4.xlarge"
                )
xgb_predictor.serializer = CSVSerializer()

predictions = xgb_predictor.predict(inf_data).decode("utf-8)
```

# [배포 가드레일](https://aws.amazon.com/ko/blogs/machine-learning/take-advantage-of-advanced-deployment-strategies-using-amazon-sagemaker-deployment-guardrails/)
![배포 가드레일](./img/%EB%B0%B0%ED%8F%AC%20%EA%B0%80%EB%93%9C%EB%A0%88%EC%9D%BC.png)

# 오토스케일링
![오토스케일링](./img/%EC%98%A4%ED%86%A0%EC%8A%A4%EC%BC%80%EC%9D%BC%EB%A7%81.png)
![오토스케일링 옵션](./img/%EC%98%A4%ED%86%A0%EC%8A%A4%EC%BC%80%EC%9D%BC%EB%A7%81%20%EC%98%B5%EC%85%98.png)
![오토스케일링 코드](./img/%EC%98%A4%ED%86%A0%EC%8A%A4%EC%BC%80%EC%9D%BC%EB%A7%81%20%EC%BD%94%EB%93%9C.png)

# [SageMaker Neo](https://github.com/neo-ai)
![sagemaker neo](./img/sagemaker%20neo.png)
![neo 코드](./img/neo%20%EC%BD%94%EB%93%9C.png)

# 체크리스트 & 꿀팁
![체크리스트](./img/%EC%B2%B4%ED%81%AC%EB%A6%AC%EC%8A%A4%ED%8A%B8.png)