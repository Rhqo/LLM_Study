# Chap. 8 고급 오픈 소스 LLM 파인튜닝

## BERT를 이용한 애니메이션 장르 다중 레이블 분류

다중 레이블 장르 예측을 위한 성능 측정 지표로 자카드 점수 사용하기

단순 파인튜닝 과정

오픈 소스 LLM 파인튜닝을 위한 일반적인 팁

Data Preparation + Feature Engineering

- 의미적 유사성 중복 제거

배치 크기 및 기울기 누적 조정

동적 패딩 사용

혼합 정밀도 훈련

모델 동결

## GPT-2를 이용한 LaTeX 생성

오픈 소스 모델을 위한 프롬프트 엔지니어링

결과

## 시난의 현명하면서도 매력적인 답변 생성기: SAWYER

1단계: 지시사항 파인튜닝

기본 작업 이해

2단계: 보상 모델 훈련

음의 로그 가능도: 잘못된 예측에 대해 지나치게 확신을 가진 모델이나 올바른 예측에 대해 확신이 부족한 모델에 불이익을 주는 방법 → 더 애매한 이해를 학습하도록 유도

3단계: (예상하는) 사용자 피드백 기반 강화 학습

## 끊임없이 변화하는 파인튜닝의 세계

PEFT: 사전 훈련된 가중치를 고정시키고 오직 몇개의 추가 가중치만을 옆에 더한다

LoRA: 추가 가중치를 더욱 슬림하게, 그것들을 컴팩트한 저랭크 행렬로 분해한다.

---

## 정리

이번 장에서는 오픈 소스 LLM의 다양한 응용 사례와 수정사항, 장단점, 잠재적인 개선점 확인했다.

**BERT를 분류 문제**에서 파인튜닝하면, `동결`, `기울기 누적`, `의미론적 다운샘플링`과 같은 기술을 사용하여 최적화하였다.

**LaTeX 방정식 생성기**는 LLM이 잘 조정되면, 수학적 표기법과 같은 전문화된 도메인서도 의미있고 맥락에 적절한 출력을 생성할 수 있음을 확인할 수 있었다.

**SAWYER**는 적은 파라미터 수를 가진 모델을 파인튜닝을 통해 최적화 하는 방법을 알 수 있었다.