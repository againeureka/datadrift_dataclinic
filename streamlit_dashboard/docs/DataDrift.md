# Types of DataDrift
## 🔎 데이터 드리프트란?


> 데이터 드리프트는 훈련 데이터와 평가 데이터 간의 분포 차이로 인해 머신러닝 모델의 성능이 저하되는 현상 

![https://spotintelligence.com/2024/04/08/data-drift-in-machine-learning/](img_files/image.png)

⇒ 머신 러닝에서 학습과 추론에 사용되는 입력 데이터의 통계적 속성이 시간이 지남에 따라 변경되는 현상

**문제**

- 드리프트 현상이 발생하면 실제 서비스 환경에서 추론 능력이 저하될 수 있음
- 이에 AI 애플리케이션 개발 시 중요한 고려사항으로 여겨짐

### 데이터 드리프트의 발생 원인은?

**Natural Changes in the Environment**

- 주변 환경의 자연스러운 변화인 계절, 경제 상황 등 같은 외부 요인으로 인해 발생할 수 있음

**Changes in User Behavior**

- 사용자 선호도, 인구 통계 등 사용자 행동은 진화할 수 있으며 기본 데이터 분포의 변화로 이어질 수 있음

**Changes in Data Collection Processes**

- 데이터 수집 방법, 데이터 전처리의 pipeline 수정 등 데이터에 변화를 가져올 수 있음

**Drift in External Factors**

- 모델 외부의 시스템이나 프로세스에서 생성된 데이터는 관련성이나 신뢰성에 영향을 미치는 변화를 겪을 수 있어 (IoT 기기의 센서 교정 변경, 타사 API 동작 변화 등) 데이터 드리프트로 이어질 수 있음

**Evolution of Business Context**

- 비즈니스 환경은 시장 경쟁, 소비자 트랜드 등 데이터 환경에 영향을 줄 수 있음

**Data Quality Issues**

- 데이터의 부정확성, 불일치 또는 편향도 데이터 품질 저하를 야기하며 이는 시간이 지남에 따라 복합적으로 기본 데이터 분포의 드리프트로 이어질 수 있음

### 드리프트 감지 방법은?

데이터 드리프트 극복을 위해 과거의 훈련 데이터가 미래의 평가 데이터와 충분히 유사할 것이라는 통상적인 머신러닝의 가정 *independent and identically distributed*을 채택하지 않고, 데이터 드리프트 현상을 빠르고 효과적으로 검출하고 대응하는 접근법이 필요

- 두 분포를 비교하는 기본적인 방법은 평균, 중앙값, 분산, 분위수 등과 같은 주요 통계를 확인
- *입력* 데이터의 경우,
    
    - 통계적인 검정, 거리 지표 등을 활용해 분포 차이 측정

        → 관찰된 변화가 통계적으로 유의미한지 평가하여 드리프트인지, 노이즈인지 등 구별하는 데에 사용
    
- *출력* 데이터의 경우,
    
   - 예측 정확도 또는 오류율의 변화를 모니터링

### 해결 방안은?

- 모델을 최신 데이터로 정기적으로 재학습[3]
- 모델을 변화하는 데이터에 지속적으로 적응시킬 필요가 있음[3]
    - online learning
        
        새로운 데이터가 들어올 때마다 모델을 업데이트하여, 최근 데이터를 반영한 예측 성능을 유지
        
    - transfer learning
        
        데이터를 주기적으로 업데이트하면서 fine-tuning을 통해 변화하는 데이터 분포에 적응


## 데이터 드리프트 종류는?

각 드리프트는 단일적으로 발생하기 보다는 여러 개의 드리프트가 동시에 발생하는 경우가 있음

### Concept Drift

> 입력 $X$와 출력 $Y$ 간의 관계 $P(Y∣X)$가 시간에 따라 변화하는 현상
> 
- 예측 모델의 정확도 감소로 이어짐[3]
- 모델이 더 이상 현재의 관계를 정확하게 반영하지 못하고 오래되었을 수 있음[3]

### Covariate Drift

> 입력 데이터(특징, feature)의 분포 $P(X)$가 변화하는 현상
> 
- 출력에 대한 조건부 분포 $P(Y∣X)$ 유지
- 입력 도메인에서 발생하는 변화로, 주로 훈련 도메인의 입력과 테스트 도메인의 입력을 통계적 검정을 통해 비교해 탐지

### **Label Drift**

> 출력 변수 $P(Y)$의 분포가 변화하는 현상
> 
- 새로운 클래스가 데이터에 등장할 때 기존 모델을 처음부터 다시 학습하지 않고 이를 처리해야 하는 문제[4]

### Feature Drift

> 개별 특징(feature)의 분포가 변화하거나, 중요도가 변화하는 현상
> 
- 특징의 중요성이나 특징과 타겟 변수 간의 관계가 변동하여 예측 모델의 성능에 영향을 미침[3]

## References

---
[1] https://spotintelligence.com/2024/04/08/data-drift-in-machine-learning/

[2] https://medium.com/@ajayverma23/understanding-and-detecting-different-types-of-drift-20d720c4727a

[3] https://ieeexplore.ieee.org/stamp/stamp.jsp?tp=&arnumber=10068710

[4] https://ieeexplore.ieee.org/stamp/stamp.jsp?tp=&arnumber=7837958